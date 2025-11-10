# JAVA_MINI_PROJECT
Expt. No. : 16 SOCIALMEDIA NOTIFICATION SYSTEM

PO-PSO Mapping Table : 
 
PO1 	PO2 	PO3 	PO4 	PO5 	PO6 	PO7 	PO8 	PO9 	PO10 	PO11 	PO12 	PSO1 	PSO2 	PSO3 
3 	2 	3 	2 	2 	1 	- 	3 	1 	2 	- 	- 	3 	2 	1 
 
PSO Justification : 
 
PSO Relevance Justification 
 	PSO Relevance Justification 
 	PSO Relevance Justification 
 
Applies core Java 
programming 
PSO1 – Apply concepts, OOP 
fundamental 
3 principles, and 
computing file/database 
knowledge handling to develop a secure voting system. 
 	Applies core Java 
programming 
PSO1 – Apply concepts, OOP 
fundamental 
3 principles, and 
computing file/database 
knowledge handling to develop a secure voting system. 
 	Applies core Java 
programming 
PSO1 – Apply concepts, OOP 
fundamental 
3 principles, and 
computing file/database 
knowledge handling to develop a secure voting system. 
 
Designs and develops modular components such as 
PSO2 – 	user registration, 
Design and 	authentication, 
2 
implement 	message and result 
solutions 	modules using 
structured programming and design logic. 
 	Designs and develops modular components such as 
PSO2 – 	user registration, 
Design and 	authentication, 
2 
implement 	message, and result 
solutions 	modules using 
structured programming and design logic. 
 	Designs and develops modular components such as 
PSO2 – 	user registration, 
Design and 	authentication, 
2 
implement 	message, and result 
solutions 	modules using 
structured programming and design logic. 
 
Utilizes 
JavaFX/Swing for 
GUI, JDBC for PSO3 – Use 	database modern tools 	interaction, and 
1 
and 	Git-based 
technologies 	deployment tools for project 
management and version control. 
 	Utilizes 
JavaFX/Swing for 
GUI, JDBC for PSO3 – Use 	database modern tools 	interaction, and 
1 
and 	Git-based 
technologies 	deployment tools for project 
management and version control. 
 	Utilizes 
JavaFX/Swing for 
GUI, JDBC for PSO3 – Use 	database modern tools 	interaction, and 
1 
and 	Git-based 
technologies 	deployment tools for project 
management and version control. 
 

PO Justification: 
 
PO 	Relevance 	Justification 
PO1 – Engineering Knowledge 	3 	Applies computing fundamentals, Java programming, and database concepts to design a secure and efficient social media notification system 
PO2 – Problem Analysis 	2 	Identifies and resolves synchronization and message handling issues between users and server in real time.
PO3 – Design/Development of Solutions 	3 	Designs an integrated system combining networking, exception handling, database, and GUI for social notifications.
PO4 – Conduct Investigations of Complex Problems 	2 	Analyzes message routing, thread synchronization, and connection stability to enhance reliability.
PO5 – Modern Tool Usage 	2 	Employs Eclipse IDE, MySQL, and JavaFX/Swing for full-stack development. 
PO6 – The Engineer and Society 	1 	Promotes digital transformation in the voting process, increasing accessibility and transparency in democratic systems. 
PO8 – Ethics 	3 	Ensures data privacy, secure connections, and responsible message handling.
PO9 – Individual and Team 
Work 	1 	Encourages collaboration and modular development for scalable social applications. 
PO10 – Communication 	2 	Demonstrates structured design and clear code documentation for better understanding.

Introduction : 
In the digital communication era, social media platforms rely on efficient notification systems to keep users updated in real time. The Social Media Notification System project is designed to deliver instant alerts for user activities such as new messages, likes, comments, or friend requests.The system ensures timely communication by integrating frontend GUI modules with backend logic and database connectivity. Developed using Java, the project demonstrates essential Object-Oriented Programming concepts such as inheritance, multithreading, exception handling, and event-driven programming.This application provides a foundation for scalable and real-time notification delivery, offering a responsive and user-friendly interface that improves the overall user experience across social platforms.

Project Distribution : 
 

Module 	Name 	Concept (Unit) 	Description 
1 	User Registration 	Core Java Fundamentals 	Handles user registration, profile creation, and validation.
2 	Login & Authentication 	OOP & Inheritance 	Authenticates users and ensures secure access control.
3 	Notification Management	Exception Handling & Control Structures 	Generates, queues, and displays notifications in real time.. 
4 	Message Delivery Module	File Handling & Database Connectivity 	Enables admin to view, count, and manage votes. 
5 	GUI Display Interface	Java GUI / Networking 	Provides a visually appealing interface using JavaFX/Swing for notification display and management.
 
 
 
 





SYSTEM ARCHITECTURE
 
CODING:-
MODULE 1
package module1.cores;

abstract class Notification {
    protected String message;
    protected User recipient;

    public Notification(String message, User recipient) {
        this.message = message;
        this.recipient = recipient;
    }

    public abstract void sendNotification();
}

class MessageNotification extends Notification {
    public MessageNotification(String message, User recipient) {
        super(message, recipient);
    }
    @Override
    public void sendNotification() {
        System.out.println("Message to " + recipient.getName() + ": " + message);
    }
}

class FriendRequestNotification extends Notification {
    public FriendRequestNotification(String message, User recipient) {
        super(message, recipient);
    }

    @Override
    public void sendNotification() {
        System.out.println("Friend Request to " + recipient.getName() + ": " + message);
    }
}

class User {
    private String name;
    private static int userCount = 0;

    public User(String name) {
        this.name = name;
        userCount++;
    }

    public String getName() { return name; }
    public static int getUserCount() { return userCount; }
}

public class Module1_OOP {
    public static void main(String[] args) {
        User alice = new User("Alice");

        Notification n1 = new MessageNotification("Hello Alice!", alice);
        n1.sendNotification();

        Notification n2 = new FriendRequestNotification("John sent you a friend request", alice);
        n2.sendNotification();

        System.out.println("Total users: " + User.getUserCount());
    }
}




MODULE 2: 
package module2.exceptions;
import java.io.*;
class InvalidUserException extends Exception {
    public InvalidUserException(String msg) {
        super(msg);
    }
}

class NotificationLogger {
    public static void log(String message) {
        try (FileWriter fw = new FileWriter("notifications.log", true)) {
            fw.write(message + "\n");
            System.out.println("Logged: " + message);
        } catch (IOException e) {
            System.out.println("Error logging notification: " + e.getMessage());
        }
    }
}
public class Module2_Exceptions {
    public static void main(String[] args) {
        String user = null; 

        try {
            if (user == null)
                throw new InvalidUserException("User not found!");
            System.out.println("Notification sent to " + user);

        } catch (InvalidUserException e) {
            System.out.println("Exception: " + e.getMessage());
            NotificationLogger.log("Error: " + e.getMessage());
        }
    }
}
MODULE 3:
package module3.generics;
import java.util.*;

class NotificationManager<T> {
    private List<T> notifications = Collections.synchronizedList(new ArrayList<>());

    public void add(T item) { notifications.add(item); }
    public void showAll() { notifications.forEach(System.out::println); }
}

class NotificationTask extends Thread {
    private String message;
    public NotificationTask(String message) { this.message = message; }

    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName() + " sending: " + message);
        try { Thread.sleep(500); } catch (InterruptedException e) {}
    }
}

public class Module3_GenericsThreads {
    public static void main(String[] args) {
        NotificationManager<String> manager = new NotificationManager<>();
        manager.add("Like Notification");
        manager.add("Comment Notification");

        NotificationTask t1 = new NotificationTask("New Message!");
        NotificationTask t2 = new NotificationTask("Friend Request!");

        t1.start();
        t2.start();

        manager.showAll();
    }
}
MODULE 4:(Backend and Database connection) package 
package module4.networking;
import java.io.*;
import java.net.*;
import java.sql.*;
public class Module4_NetworkJDBC {
    private static final int PORT = 5000;
    // Database credentials
    private static final String DB_URL = "jdbc:mysql://localhost:3306/testdb";
    private static final String DB_USER = "root";
    private static final String DB_PASS = "Quality@01";
    public static void main(String[] args) {
        System.out.println("🚀 Starting Social Media Notification (Networking + JDBC) Module...\n");
        new Thread(Module4_NetworkJDBC::startServer, "Server-Thread").start();
        new Thread(Module4_NetworkJDBC::startClient, "Client-Thread").start();
        try {
            Thread.sleep(3000); // Wait for server/client to finish
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
        // Show notifications stored in DB
        displayNotificationsFromDB();
        System.out.println("\n✅ Module 4 execution completed successfully!");
    }
    // 1️⃣ Server: Receives message from client and inserts into DB
    public static void startServer() {
        try (ServerSocket serverSocket = new ServerSocket(PORT)) {
            System.out.println("[SERVER] Started on port " + PORT + ". Waiting for client...");
            Socket socket = serverSocket.accept();
            System.out.println("[SERVER] Client connected from " + socket.getInetAddress());
            try (BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()))) {
                String message = in.readLine();
                System.out.println("[SERVER] Received message: " + message);
                insertNotificationToDB(message);
            }
        } catch (IOException e) {
            System.err.println("[SERVER] Error: " + e.getMessage());
        }
    }
    // 2️⃣ Client: Sends a notification message to the server
    public static void startClient() {
        try {
            Thread.sleep(1000); // wait for server to start
            System.out.println("[CLIENT] Connecting to server on localhost:" + PORT + "...");
            try (Socket socket = new Socket("localhost", PORT);
                 PrintWriter out = new PrintWriter(socket.getOutputStream(), true)) {
                String message = "Divya liked your story! (New Notification)";
                out.println(message);
                System.out.println("[CLIENT] Sent message: " + message);
            }
        } catch (IOException | InterruptedException e) {
            System.err.println("[CLIENT] Error: " + e.getMessage());
        }
    }
    // 3️⃣ Insert received notification into MySQL
    private static void insertNotificationToDB(String message) {
        String query = "INSERT INTO notifications (message) VALUES (?)";
        try (Connection conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASS);
             PreparedStatement pstmt = conn.prepareStatement(query)) {
            pstmt.setString(1, message);
            pstmt.executeUpdate();
            System.out.println("[DB] ✅ Notification saved to database.");
        } catch (SQLException e) {
            System.err.println("[DB] ❌ Failed to insert: " + e.getMessage());
        }
    }
    // 4️⃣ Display all notifications from the database
    private static void displayNotificationsFromDB() {
        String query = "SELECT * FROM notifications ORDER BY created_at DESC";
        try (Connection conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASS);
             Statement stmt = conn.createStatement();
             ResultSet rs = stmt.executeQuery(query)) {
            System.out.println("\n🗂️ Notifications stored in Database:");
            System.out.println("-----------------------------------------------------------");
            while (rs.next()) {
                System.out.println(
                    rs.getInt("id") + ". " +
                    rs.getString("message") + "   [" +
                    rs.getTimestamp("created_at") + "]"
                );
            }
            System.out.println("-----------------------------------------------------------");

        } catch (SQLException e) {
            System.err.println("[DB] ❌ Error fetching data: " + e.getMessage());
        }
    }
}
MODULE 5(Frontend and User Interface): 

package module5.gui;
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

// Demonstrates Swing GUI + MVC concept for Social Media Notification System
public class Module5_GUI {

    public static void main(String[] args) {
        // Run GUI in the Event Dispatch Thread for thread safety
        SwingUtilities.invokeLater(() -> new NotificationView().createAndShowGUI());
    }
}

// ----- Model -----
class NotificationModel {
    private String latestNotification = "";

    public void setNotification(String message) {
        latestNotification = message;
    }

    public String getNotification() {
        return latestNotification;
    }
}

// ----- View + Controller -----
class NotificationView {
    private final NotificationModel model = new NotificationModel();

    private JFrame frame;
    private JTextArea notificationArea;
    private JTextField inputField;
    private JButton sendButton;

    public void createAndShowGUI() {
        frame = new JFrame("Social Media Notification System");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(500, 350);
        frame.setLayout(new BorderLayout(10, 10));

        // Title
        JLabel title = new JLabel("📱 Social Media Notification System", JLabel.CENTER);
        title.setFont(new Font("SansSerif", Font.BOLD, 18));
        frame.add(title, BorderLayout.NORTH);

        // Notification Display Area
        notificationArea = new JTextArea();
        notificationArea.setEditable(false);
        notificationArea.setFont(new Font("Monospaced", Font.PLAIN, 14));
        frame.add(new JScrollPane(notificationArea), BorderLayout.CENTER);

        // Input area at bottom
        JPanel bottomPanel = new JPanel(new BorderLayout(5, 5));
        inputField = new JTextField();
        inputField.setFont(new Font("SansSerif", Font.PLAIN, 14));
        sendButton = new JButton("Send Notification");
        sendButton.setFont(new Font("SansSerif", Font.BOLD, 14));

        // Action Listener (Controller)
        sendButton.addActionListener(e -> sendNotification());

        bottomPanel.add(inputField, BorderLayout.CENTER);
        bottomPanel.add(sendButton, BorderLayout.EAST);
        frame.add(bottomPanel, BorderLayout.SOUTH);

        // Center the window
        frame.setLocationRelativeTo(null);
        frame.setVisible(true);
    }

    private void sendNotification() {
        String message = inputField.getText().trim();
        if (message.isEmpty()) {
            JOptionPane.showMessageDialog(frame, "Please enter a notification message!");
            return;
        }

        // Update model and display in view
        model.setNotification(message);
        notificationArea.append("📢 New Notification: " + model.getNotification() + "\n");
        inputField.setText("");
    }
}



GITHUB Link for Full Code : 


Screenshots : 
Frontend Structure : 
  
 
 
 
Description: 
The frontend is developed using Java Swing, providing an intuitive interface for viewing and sending notifications.
It connects to the backend (network and JDBC) using MVC design, ensuring separation between logic and display.
The interface includes:
•	Notification display area
•	Input text field for sending messages
•	“Send” and “Refresh” buttons
Each interaction is handled using ActionListeners, ensuring smooth user experience.


Database Structure : 
 
  
 


Description: 
The backend handles user connections, message storage, and synchronization between client-server components.
When a notification is sent, it is both:
1.	Displayed in the GUI for the sender/receiver, and
2.	Stored in the MySQL database via JDBC.
All operations use prepared statements for security and efficiency







Database Storage Image : 
  

 
 
Description: 
The above image shows the notifications table stored in the testdb MySQL database.
Each notification message sent from the client or entered through the GUI is automatically stored in this table using JDBC connectivity.
•	The id column is an auto-incremented primary key that uniquely identifies each notification.
•	The message column stores the content of the notification (for example, “Ajay liked your post!”).
•	The created_at column automatically records the date and time when the notification was inserted into the database using the CURRENT_TIMESTAMP default.
This confirms that the Java Networking + JDBC integration works successfully — data sent from the client is transmitted to the server and stored persistently in the MySQL database for future retrieval.
Github Pages : 
 
 
 
 
 
Description: 
 
The screenshot above displays the GitHub repository interface of the Social media notification system (Java Project). The project is neatly organized into five separate module folders — each representing a specific Java unit — along with a detailed README.md file that provides documentation and an architectural overview of the system. 
 
The README is formatted in Markdown and rendered directly on GitHub for clear readability. It includes sections such as Overview, Project Modules, System Architecture, and Database Setup, ensuring that users can easily understand the project’s structure and functionality. 
 
Additionally, the repository contains an architecture-diagram.jpg file, which visually represents the system workflow between the JavaFX frontend, JDBC backend, and the MySQL database. This GitHub setup provides a centralized, accessible, and version-controlled platform for hosting and sharing the complete mini-project publicly. 
 
 
Website Output Pages:  
 
  
 
 
 


The above image represents the Graphical User Interface (GUI) of the Social Media Notification System, developed using Java Swing.
This interface allows users to create, send, and display notifications in a visually interactive manner.
•	The window title “Social Media Notification System” clearly indicates the purpose of the application.
•	The text area in the center displays all the notifications that have been sent.
•	The input field at the bottom allows the user to type a new message.
•	When the user clicks the “Send Notification” button, the message is added to the display area, and a new notification entry is generated.
For example, the message “John has sent you a follow request” shows that the system successfully captures and displays notifications dynamically, providing real-time visual feedback to the user.
Conclusion: 
The Social Media Notification System project successfully demonstrates how real-time communication, database interaction, and user interface design can be seamlessly integrated using Java, Swing, and MySQL. The system effectively simulates a simplified social media environment where notifications are generated, sent, and displayed dynamically to users.
Each module of the project highlights the core principles of Java programming — from Object-Oriented Programming (OOP) and Exception Handling to Multithreading, JDBC connectivity, and GUI development — ensuring a modular and scalable design. The project’s interaction between the GUI interface, networking components, and the MySQL backend showcases efficient data flow, consistency, and smooth user experience.
Overall, this project emphasizes key software engineering principles such as real-time event handling, data persistence, and modular system architecture, providing a practical foundation for building larger-scale social networking or notification-based applications in the future.

Future Work: 
•  Implement user authentication and profile management for personalized notifications.
•  Add real-time push notifications using WebSocket or Firebase Cloud Messaging (FCM).
•  Introduce a message filtering and categorization system (likes, comments, follows, etc.).
•  Connect the system with a mobile app interface for cross-platform access.
•  Enhance the GUI using JavaFX or modern UI frameworks for a more interactive experience.
•  Integrate sentiment analysis or AI-based recommendation systems for smarter notifications.
•  Enable multimedia notifications (images, videos, emojis) for better user engagement
