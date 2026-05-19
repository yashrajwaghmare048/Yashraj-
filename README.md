Here is the complete Java code from your document, organized cleanly in text format and in the exact order of appearance.
## Part A: Assignment No. 1
```java
import java.util.InputMismatchException;
import java.util.Scanner;

public class Calculator { 
    static double addition(double a, double b) { 
        return a + b;
    }

    static double subtraction(double a, double b) { 
        return a - b;
    }

    static double multiplication(double a, double b) { 
        return a * b;
    }

    static double division(double a, double b) { 
        if (b == 0) { 
            throw new ArithmeticException("Division by zero is not allowed.");
        }
        return a / b; 
    }

    public static void main(String[] args) { 
        Scanner sc = new Scanner(System.in);
        int choice;
        boolean continueCalc = true; 
        
        do { 
            try { 
                System.out.println("\n--- Calculator Menu ---"); 
                System.out.println("1. Addition");
                System.out.println("2. Subtraction"); 
                System.out.println("3. Multiplication");
                System.out.println("4. Division");
                System.out.println("5. Exit");
                System.out.print("Enter your choice: ");
                choice = sc.nextInt();

                if (choice == 5) { 
                    System.out.println("Exiting Calculator. Thank you!");
                    break;
                }

                System.out.print("Enter first number: ");
                double num1 = sc.nextDouble();
                System.out.print("Enter second number: ");
                double num2 = sc.nextDouble();
                double result;

                switch (choice) { 
                    case 1: 
                        result = addition(num1, num2);
                        System.out.println("Result = " + result); 
                        break;
                    case 2: 
                        result = subtraction(num1, num2);
                        System.out.println("Result = " + result);
                        break;
                    case 3: 
                        result = multiplication(num1, num2);
                        System.out.println("Result = " + result);
                        break;
                    case 4: 
                        result = division(num1, num2);
                        System.out.println("Result = " + result);
                        break;
                    default: 
                        System.out.println("Invalid choice! Please select 1 to 5.");
                }
            }
            catch (InputMismatchException e) { 
                System.out.println("Invalid input! Please enter numeric values only.");
                sc.nextLine(); // clear buffer 
            }
            catch (ArithmeticException e) { 
                System.out.println("Error: " + e.getMessage());
            }
        } while (continueCalc);

        sc.close(); 
    } 
}

```
## Assignment No. 2
```java
import java.util.Scanner;

class Product { 
    String name; 
    double price; 
    int quantity;

    // Constructor 1: Default Product
    Product() { 
        name = "Unknown"; 
        price = 0.0;
        quantity = 0; 
    }

    // Constructor 2: Initialize with name and price
    Product(String name, double price) { 
        this.name = name; 
        this.price = price;
        quantity = 1; // default quantity 
    }

    // Constructor 3: Initialize with full details
    Product(String name, double price, int quantity) { 
        this.name = name;
        this.price = price; 
        this.quantity = quantity; 
    }

    double getTotalCost() { 
        return price * quantity;
    }

    // Static method to apply discount
    static double applyDiscount(double total) { 
        if (total > 15000) return total - total * 0.25;
        else if (total > 10000) return total - total * 0.20;
        else if (total > 5000) return total - total * 0.15;
        else return total;
    }

    // Method to display product details
    void displayProduct() { 
        System.out.println(name + " | Price: " + price + " | Quantity: " + quantity + " | Total: " + (price * quantity));
    }
}

public class Ecommerce { 
    public static void main(String[] args) { 
        Scanner sc = new Scanner(System.in);
        Product p1 = new Product("Powerbank", 800);
        Product p2 = new Product("Headphones", 150, 2);

        // User input
        System.out.print("Enter product name: ");
        String name = sc.nextLine();
        System.out.print("Enter product price: ");
        double price = sc.nextDouble();
        System.out.print("Enter quantity: ");
        int quantity = sc.nextInt();
        
        Product userProduct = new Product(name, price, quantity);

        // Display order summary
        System.out.println("\nOrder Summary:");
        p1.displayProduct();
        p2.displayProduct();
        userProduct.displayProduct();

        double totalCost = p1.getTotalCost() + p2.getTotalCost() + userProduct.getTotalCost();
        double finalAmount = Product.applyDiscount(totalCost);

        System.out.println("\nTotal Cost Before Discount: " + totalCost);
        System.out.println("Final Price After Discount: " + finalAmount);
        System.out.println("Thank you for shopping!");
        sc.close();
    }
}

```
## Assignment No. 3
```java
import java.lang.Math;

public class OverloadingDemo {
    int power(int base, int exp) { 
        int result = 1;
        for (int i = 1; i <= exp; i++) { 
            result *= base; 
        }
        return result;
    }

    double power(double base, int exp) { 
        double result = 1;
        for (int i = 1; i <= exp; i++) { 
            result *= base; 
        }
        return result; 
    }

    int absolute(int num) {
        return Math.abs(num);
    }

    double absolute(double num) { 
        return Math.abs(num);
    }
}

class TestOverloadingDemo { 
    public static void main(String[] args) { 
        OverloadingDemo c = new OverloadingDemo();
        System.out.println("Power (int): " + c.power(2, 3));
        System.out.println("Power (double): " + c.power(2.5, 3));
        System.out.println("Absolute (int): " + c.absolute(-10));
        System.out.println("Absolute (double): " + c.absolute(-15.75));
    }
}

```
## Assignment No. 4
```java
import java.util.Scanner;

class Book { 
    String title;
    boolean isIssued;
    static int totalBooks = 0;

    public Book(String title) { 
        this.title = title;
        this.isIssued = false;
        totalBooks++;
    }

    void issueBook() { 
        if (!isIssued) { 
            isIssued = true;
            System.out.println("Book '" + title + "' has been issued.");
        }
        else { 
            System.out.println("Book \"" + title + "\" is already issued.");
        }
    }

    public void returnBook() { 
        if (isIssued) { 
            isIssued = false;
            System.out.println("Book '" + title + "' has been returned.");
        }
        else { 
            System.out.println("Book " + title + " was not issued.");
        }
    }

    void displayBook() {
        System.out.println(title + " | " + (isIssued ? "Issued" : "Available"));
    }

    public static void displayTotalBooks() { 
        System.out.println("Total Books in Library: " + totalBooks);
    }
}

public class LibrarySystem {
    public static void main(String[] args) { 
        Scanner scanner = new Scanner(System.in);
        Book[] library = new Book[5];
        int count = 0;

        while (true) {
            System.out.println("\nLibrary Management System");
            System.out.println("1. Add Book");
            System.out.println("2. Issue Book");
            System.out.println("3. Return Book");
            System.out.println("4. View Books");
            System.out.println("5. Check Total Books");
            System.out.println("6. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine();

            switch (choice) {
                case 1:
                    System.out.print("Enter Book Title: ");
                    String title = scanner.nextLine();
                    library[count] = new Book(title);
                    count++;
                    System.out.println("Book added successfully.");
                    break;
                case 2:
                    System.out.print("Enter Book Number to Issue (1-" + count + "): ");
                    int issueNum = scanner.nextInt();
                    library[issueNum - 1].issueBook();
                    break;
                case 3:
                    System.out.print("Enter Book Number to Return (1-" + count + "): ");
                    int returnNum = scanner.nextInt();
                    library[returnNum - 1].returnBook();
                    break;
                case 4:
                    System.out.println("\nLibrary Books:");
                    for (int i = 0; i < count; i++) { 
                        System.out.print((i + 1) + ". ");
                        library[i].displayBook(); 
                    }
                    break;
                case 5:
                    Book.displayTotalBooks();
                    break;
                case 6:
                    System.out.println("Exiting the system. Thank you!");
                    scanner.close();
                    return;
                default: 
                    System.out.println("Invalid choice. Try again.");
            }
        }
    }
}

```
## Part B: Assignment No. 1
```java
class Animal {
    void eat() {
        System.out.println("Animal is eating.");
    }
    void sleep() { 
        System.out.println("Animal is sleeping.");
    }
}

class Dog extends Animal { 
    void bark() {
        System.out.println("Dog is barking.");
    }
    void showActions(){
        System.out.println("--- Dog Actions ---");
        eat();
        sleep();
        bark();
    }
}

public class SingleInheritanceDemo {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.showActions();
    }
}

```
## Assignment No. 2
```java
interface Shape {
    void draw();
    double area();
}

class Circle implements Shape {
    double radius;
    Circle(double radius) {
        this.radius = radius; 
    }
    public void draw() { 
        System.out.println("Drawing a Circle");
    }
    public double area() {
        return Math.PI * radius * radius;
    }
}

class Rectangle implements Shape {
    double length, width;
    Rectangle(double length, double width) {
        this.length = length; 
        this.width = width;
    }
    public void draw() { 
        System.out.println("Drawing a Rectangle");
    }
    public double area() {
        return length * width;
    }
}

public class InterfacePolymorphismDemo { 
    public static void main(String[] args) {
        Shape s;
        s = new Circle(4.5);
        s.draw();
        System.out.println("Circle Area: " + s.area());
        System.out.println();
        
        s = new Rectangle(5, 8);
        s.draw();
        System.out.println("Rectangle Area: " + s.area());
    }
}

```
## Assignment No. 4
```java
import java.util.Scanner; 

class ATM { 
    private double balance; 
    ATM(double initialBalance) {
        balance = initialBalance;
    } 
    void checkBalance() {
        System.out.println("Current Balance: ₹" + balance); 
    } 
    void deposit(double amount) { 
        if (amount <= 0) { 
            throw new IllegalArgumentException("Deposit amount must be positive.");
        } 
        balance += amount;
        System.out.println("₹" + amount + " deposited successfully.");
    } 
    void withdraw(double amount) { 
        if (amount <= 0) { 
            throw new IllegalArgumentException("Withdrawal amount must be positive.");
        } 
        if (amount > balance) { 
            throw new ArithmeticException("Insufficient funds.");
        } 
        balance -= amount; 
        System.out.println("₹" + amount + " withdrawn successfully.");
    }
}

public class ATMSimulator { 
    public static void main(String[] args) { 
        Scanner sc = new Scanner(System.in);
        ATM atm = new ATM(5000);
        int choice;
        
        do { 
            System.out.println("\n----- ATM MENU -----");
            System.out.println("1. Check Balance"); 
            System.out.println("2. Deposit Money"); 
            System.out.println("3. Withdraw Money"); 
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            
            try { 
                choice = sc.nextInt();
                switch (choice) { 
                    case 1: 
                        atm.checkBalance();
                        break;
                    case 2: 
                        System.out.print("Enter deposit amount: ");
                        double depositAmount = sc.nextDouble();
                        atm.deposit(depositAmount); 
                        break;
                    case 3: 
                        System.out.print("Enter withdrawal amount: "); 
                        double withdrawAmount = sc.nextDouble(); 
                        atm.withdraw(withdrawAmount); 
                        break;
                    case 4:
                        System.out.println("Thank you for using ATM.");
                        sc.close();
                        return;
                    default: 
                        throw new IllegalArgumentException("Invalid menu choice.");
                }
            }
            catch (ArithmeticException e) { 
                System.out.println("Error: " + e.getMessage());
            } 
            catch (IllegalArgumentException e) { 
                System.out.println("Error: " + e.getMessage());
            } 
            catch (Exception e) { 
                System.out.println("Error: Invalid input. Please enter numbers only.");
                sc.nextLine(); // clear invalid input
            }
            finally {
                System.out.println("Transaction completed.\n"); 
            } 
        } while (true);
    } 
}

```
## Assignment No. 6
```java
import java.util.Random; 

class Stock {
    private double price; 
    void setPrice(double price) {
        this.price = price;
    } 
    double getPrice() {
        return price; 
    } 
} 

class PriceFetcher extends Thread {
    private Stock stock; 
    PriceFetcher(Stock stock) {
        this.stock = stock;
    }
    public void run() {
        Random random = new Random(); 
        for (int i = 1; i <= 5; i++) {
            try { 
                double newPrice = 100 + random.nextInt(50);
                stock.setPrice(newPrice);
                System.out.println("Fetched stock price: ₹" + newPrice); 
                Thread.sleep(1000); 
            } 
            catch (InterruptedException e) { 
                System.out.println("Fetcher thread interrupted");
            }
        }
    }
}

class PriceDisplay extends Thread { 
    private Stock stock; 
    PriceDisplay(Stock stock) { 
        this.stock = stock;
    } 
    public void run() {
        for (int i = 1; i <= 5; i++) {
            try { 
                System.out.println("Displayed stock price: ₹" + stock.getPrice());
                Thread.sleep(1000);
            } 
            catch (InterruptedException e) { 
                System.out.println("Display thread interrupted"); 
            }
        }
    }
}

public class StockMonitor { 
    public static void main(String[] args) {
        Stock stock = new Stock();
        PriceFetcher fetcher = new PriceFetcher(stock);
        PriceDisplay display = new PriceDisplay(stock); 
        
        fetcher.start(); 
        display.start();
        
        try { 
            fetcher.join();
            display.join(); 
        } 
        catch (InterruptedException e) { 
            System.out.println("Main thread interrupted");
        } 
        System.out.println("Stock monitoring completed.");
    } 
}

```
## PART C-2
### Main.java
```java
import java.util.Scanner; 

public class Main { 
    public static void main(String[] args) { 
        Scanner sc = new Scanner(System.in);
        StudentDAO dao = new StudentDAO(); 
        
        while (true) { 
            System.out.println("\n--- Student Management ---"); 
            System.out.println("1. Add Student"); 
            System.out.println("2. View Students");
            System.out.println("3. Update Student"); 
            System.out.println("4. Delete Student"); 
            System.out.println("5. Exit"); 
            System.out.print("Enter choice: "); 
            int choice = sc.nextInt();
            
            switch (choice) { 
                case 1: 
                    sc.nextLine(); 
                    System.out.print("Name: "); 
                    String name = sc.nextLine(); 
                    System.out.print("Email: "); 
                    String email = sc.nextLine(); 
                    System.out.print("Course: ");
                    String course = sc.nextLine(); 
                    dao.addStudent(new Student(name, email, course)); 
                    break; 
                case 2: 
                    dao.viewStudents(); 
                    break; 
                case 3: 
                    System.out.print("Enter ID: ");
                    int id = sc.nextInt(); 
                    sc.nextLine(); 
                    System.out.print("New Course: "); 
                    String newCourse = sc.nextLine(); 
                    dao.updateStudent(id, newCourse); 
                    break; 
                case 4: 
                    System.out.print("Enter ID: ");
                    int deleteId = sc.nextInt(); 
                    dao.deleteStudent(deleteId); 
                    break; 
                case 5: 
                    System.out.println("Exiting..."); 
                    sc.close(); 
                    return; 
                default: 
                    System.out.println("Invalid choice!");
            } 
        } 
    } 
}

```
### Student.java
```java
public class Student { 
    private int id; 
    private String name; 
    private String email; 
    private String course;

    public Student(String name, String email, String course) { 
        this.name = name; 
        this.email = email; 
        this.course = course;
    } 
    
    public Student(int id, String name, String email, String course) { 
        this.id = id; 
        this.name = name; 
        this.email = email;
        this.course = course; 
    } 
    
    public int getId() { return id; } 
    public String getName() { return name; } 
    public String getEmail() { return email; } 
    public String getCourse() { return course; } 
}

```
### StudentDAO.java
```java
import java.sql.*; 

public class StudentDAO { 
    // CREATE 
    public void addStudent(Student student) { 
        String query = "INSERT INTO students (name, email, course) VALUES (?, ?, ?)";
        try (Connection conn = DBConnection.getConnection()) { 
            conn.setAutoCommit(false); // Start transaction 
            try (PreparedStatement pst = conn.prepareStatement(query)) { 
                pst.setString(1, student.getName()); 
                pst.setString(2, student.getEmail());
                pst.setString(3, student.getCourse()); 
                pst.executeUpdate(); 
                conn.commit(); // Commit transaction 
                System.out.println("Student added successfully!"); 
            } catch (SQLException e) { 
                conn.rollback(); // Rollback on error 
                System.out.println("Transaction rolled back!"); 
                e.printStackTrace(); 
            } 
        } catch (SQLException e) { 
            Sys# Yashraj-
