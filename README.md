Download Link: https://assignmentchef.com/product/solved-cmsc204-assignment-7
<br>
You will be designing a chat room service.

Your program will consist of three main parts:

<ol>

 <li>A GUI Controller – this will have instructions, and buttons to start the server, to start each client, and to exit.</li>

 <li>Client – The Chat application for each user. Each client will run in its own thread. Start this class after the Server is running.</li>

 <li>Server – Manages the clients, checking their screen names and echo-printing their messages to the other clients. Start this class before the client.</li>

</ol>

Step1

<strong>Operation </strong>(what the user sees):

When the application starts, the user is presented with a window that has a list of instructions and three buttons: “Start Server”, “Start Client”, and “Exit”.

The user starts the server first.  If they attempt to start a client before a server, or to start more than one server, an error message is given.

Then the user starts a client.  The user is asked for a screen name.  If the name is already in use in this session an error message is given the user is re-asked for a screen name, or if the user selects “Cancel”, the user is re-asked for a screen name.  The user can start multiple clients.

When a user successfully enters a screen name, a window is shown where the user can type in a message.  When the user enters a message, it is rebroadcast to all users.

<strong>Specifications</strong> (what the programmer does):

<ul>

 <li>Create a GUI Controller: this will have instructions, and buttons to start the server, to start each client, and to exit.

  <ol>

   <li>Instructions will be several labels</li>

   <li>Start Server Button:

    <ol>

     <li>This button will have a mnemonic and a tooltip.</li>

     <li>When this button is selected, create a new ChatServerExec.</li>

    </ol></li>

  </ol></li>

 <li>Then call the ChatServerExec.startServer method with the port number as an argument if the server has not yet been created.</li>

</ul>

<ol>

 <li>The GUI controller will maintain a sentinel that specifies whether or not the server has been started yet, and display a JOptionPane message if it has.</li>

</ol>

<ol>

 <li>Start Client Button:

  <ol>

   <li>This button will have a mnemonic and a tooltip.</li>

   <li>Each time the “Start Client” button is selected in the GUI, create a new ChatClientExec.</li>

  </ol></li>

</ol>

<ul>

 <li>Then call the ChatClientExec.startClient method with the port number as an argument</li>

</ul>

<ol>

 <li>Exit Button:

  <ol>

   <li>This button will have a mnemonic and a tooltip.</li>

   <li>When selected, the server and any clients, along with the controller GUI, will close.</li>

  </ol></li>

</ol>

<ul>

 <li>Client – The Chat application for each user. The client will consist of an executive (ChatClientExec) and ChatClient classes.

  <ol>

   <li>Start ChatClientExec from the GUI after the Server is running.</li>

   <li>ChatClientExec will create a new ChatClient and run it in its own thread.</li>

   <li>The ChatClient process will create a new Stage, which will produce a separate GUI for each client.</li>

   <li>The user will be asked to enter a screen name</li>

   <li>When the screen name is accepted, the client’s chat textbox will be enabled. When the user types into the textbox, the client will transmit the message to the server.</li>

   <li>When the client receives messages from the server, it will be displayed in the client’s textarea.</li>

  </ol></li>

 <li>Server – Manages the clients.

  <ol>

   <li>Maintain a list of screen names in use in this session and check new names for duplication.</li>

   <li>Maintain a list of PrintWriter objects, and iterate through them to echo-print clients’ messages.</li>

   <li>Start this class before the client.</li>

  </ol></li>

 <li>Assumptions:

  <ol>

   <li>It is assumed that the GUI, the server, and clients will be run on the same computer.</li>

   <li>It is assumed that synchronization of objects with locks or conditions will not be needed.</li>

  </ol></li>

 <li>Application Protocol. The Chat Protocol is as follows. (<strong>Bold font</strong> indicates strings sent between server and clients)</li>

</ul>




<table>

 <tbody>

  <tr>

   <td width="134"><em>Condition</em></td>

   <td width="174"><em>Server Action</em></td>

   <td width="258"><em>Client Action</em></td>

  </tr>

  <tr>

   <td width="134">Client starts, server accepts client</td>

   <td width="174">Sends “<strong>SUBMITNAME</strong>”</td>

   <td width="258">Receives “<strong>SUBMITNAME</strong>” and asks user for screen name</td>

  </tr>

  <tr>

   <td width="134">Client has received “SUBMITNAME”</td>

   <td width="174">Server blocks waiting for input</td>

   <td width="258">Client sends <strong>screen name</strong></td>

  </tr>

  <tr>

   <td width="134">Client has sent screen name</td>

   <td width="174">Receives client <strong>screen name</strong>, checks for duplicates, sends “<strong>NAMEACCEPTED</strong>“</td>

   <td width="258">Client blocks waiting for input</td>

  </tr>

  <tr>

   <td width="134">Server has sent “NAMEACCEPTED”</td>

   <td width="174">Server  blocks waiting for input</td>

   <td width="258">Receives “<strong>NAMEACCEPTED</strong>“, sets message text field to “editable”</td>

  </tr>

  <tr>

   <td width="134">Client has received “NAMEACCEPTED”</td>

   <td width="174">Server  blocks waiting for input</td>

   <td width="258">Client types a message in text field, sends <strong>message</strong></td>

  </tr>

  <tr>

   <td width="134">Client has sent message</td>

   <td width="174">Receives client <strong>message</strong>, sends “<strong>MESSAGE <em>name: message</em></strong>” to all clients</td>

   <td width="258">Client blocks waiting for input</td>

  </tr>

  <tr>

   <td width="134">Server has sent message to all clients</td>

   <td width="174">Server blocks waiting for input</td>

   <td width="258">Client receives “<strong>MESSAGE <em>name: message</em></strong>” and prints to text area.</td>

  </tr>

 </tbody>

</table>




<u>Deliverables</u>:

Java files – The src folder with your client and server and test (.java) files

Javadoc files – The doc folder with your javadoc for student generated files

UML Class Diagram (an image, not the proprietary format, must be a .jpg or .pdf)<em> </em>

<u>Deliverable format</u>: The above deliverables will be packaged as follows. Two compressed files in the following formats:

LastNameFirstName_AssignmentX_<strong>Complete</strong>.zip [a compressed file containing the

following]

UML.jpg

Assignment 7 Checklist (filled in with YES or NO or ?)

doc [a directory] <em>please include the entire doc folder</em>

<em>generated files</em>

file1.html (example)

file2.html (example)

src [a directory] <em>contains</em><em> </em><em>your</em><em> </em><em>client and server (.</em><em>java</em><em>) files.  Include all </em>

<em>files that </em><em>are needed to run your assignment, including those given to you</em>

File1.java (example)

File2.java (example)

File_Test.java (example)

LastNameFirstName_AssignmentX_<strong>Moss</strong>.zip [a compressed file containing only the

following]

<em>contains .java file which includes student generated client and server (.java) files – </em><em>NO FOLDERS!!</em>

File1.java (example)

File2.java (example)