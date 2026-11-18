# Prog6112-exam
An exam

import javax.swing.*;
import java.awt.*;

public class HospitalInspections extends JFrame {

    //Components of the code
    private JTextField txtHospitalName;
    private JTextField txtHospitalLocation;
    private JComboBox<String> cmbYears;
    private JButton btnSave, btnPrint, btnClear;
    private JList<String> lstHospitals;
    private DefaultListModel<String> listModel;

    // Arrays to store a maximum of five hospital records
    private final String[] hospitalNames = new String[5];
    private final String[] hospitalLocations = new String[5];
    private final int[] inspectionYears = new int[5];

    // Number of hospital records saved
    private int count = 0;

    // Constructor
    public HospitalInspections() {

        setTitle("Hospital Inspections");
        setSize(480, 430);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        // The main panel of the report 
        JPanel mainPanel = new JPanel();
        mainPanel.setLayout(new BorderLayout(10, 10));
        mainPanel.setBorder(
            BorderFactory.createEmptyBorder(15, 15, 15, 15)
        );

        // Panel for hospital information
        JPanel inputPanel = new JPanel(new GridLayout(4, 2, 10, 10));

        txtHospitalName = new JTextField();
        txtHospitalLocation = new JTextField();

        // Combo box containing 1 to 5 years
        String[] years = {
            "1 Year", "2 Years", "3 Years",
            "4 Years", "5 Years"
        };

        cmbYears = new JComboBox<>(years);

        btnSave = new JButton("SAVE");

        inputPanel.add(new JLabel("Hospital Name:"));
        inputPanel.add(txtHospitalName);

        inputPanel.add(new JLabel("Hospital Location:"));
        inputPanel.add(txtHospitalLocation);

        inputPanel.add(new JLabel("Years since inspection:"));
        inputPanel.add(cmbYears);

        inputPanel.add(new JLabel(""));
        inputPanel.add(btnSave);

        mainPanel.add(inputPanel, BorderLayout.NORTH);

        // List to display hospital inspections
        listModel = new DefaultListModel<>();
        lstHospitals = new JList<>(listModel);

        JScrollPane scrollPane = new JScrollPane(lstHospitals);
        mainPanel.add(scrollPane, BorderLayout.CENTER);

        // Print and clear Buttons
        JPanel buttonPanel = new JPanel(new GridLayout(1, 2, 10, 10));

        btnPrint = new JButton("PRINT");
        btnClear = new JButton("CLEAR");

        buttonPanel.add(btnPrint);
        buttonPanel.add(btnClear);

        mainPanel.add(buttonPanel, BorderLayout.SOUTH);

        add(mainPanel);

        // Create the menu
        JMenuBar menuBar = new JMenuBar();

        JMenu fileMenu = new JMenu("File");
        JMenu toolsMenu = new JMenu("Tools");

        JMenuItem exitItem = new JMenuItem("Exit");
        JMenuItem saveItem = new JMenuItem("Save");
        JMenuItem printItem = new JMenuItem("Print");
        JMenuItem clearItem = new JMenuItem("Clear");

        fileMenu.add(exitItem);

        toolsMenu.add(saveItem);
        toolsMenu.add(printItem);
        toolsMenu.add(clearItem);

        menuBar.add(fileMenu);
        menuBar.add(toolsMenu);

        setJMenuBar(menuBar);

        // Enter the buttons handlers
        btnSave.addActionListener(e -> saveHospital());
        btnPrint.addActionListener(e -> printHospitals());
        btnClear.addActionListener(e -> clearControls());

        // Enter the menu handlers
        saveItem.addActionListener(e -> saveHospital());
        printItem.addActionListener(e -> printHospitals());
        clearItem.addActionListener(e -> clearControls());

        exitItem.addActionListener(e -> System.exit(0));
    }

    // Save hospital inspection details into arrays
    private void saveHospital() {

        // Check whether the maximum number is reached
        if (count >= 5) {
            JOptionPane.showMessageDialog(
                this,
                "Maximum inspection count reached!",
                "Message",
                JOptionPane.INFORMATION_MESSAGE
            );
            return;
        }

        String name = txtHospitalName.getText().trim();
        String location = txtHospitalLocation.getText().trim();

        int years = cmbYears.getSelectedIndex() + 1;

        // Validate the hospital name and location
        if (name.isEmpty() || location.isEmpty()) {
            JOptionPane.showMessageDialog(
                this,
                "Please enter hospital name and location.",
                "Input Error",
                JOptionPane.ERROR_MESSAGE
            );
            return;
        }

        // Store details in arrays
        hospitalNames[count] = name;
        hospitalLocations[count] = location;
        inspectionYears[count] = years;

        count++;

        JOptionPane.showMessageDialog(
            this,
            "Hospital inspection saved successfully!"
        );

        // Clear input fields for the next hospital
        txtHospitalName.setText("");
        txtHospitalLocation.setText("");
        cmbYears.setSelectedIndex(0);
        txtHospitalName.requestFocusInWindow();
    }

    // Display all saved hospital inspections
    private void printHospitals() {

        listModel.clear();
//If method 
        if (count == 0) {
            JOptionPane.showMessageDialog(
                this,
                "No hospital inspections have been saved."
            );
            return;
        }

        // Retrieve and display records from arrays
        for (int i = 0; i < count; i++) {

            listModel.addElement(
                "Hospital Name: " + hospitalNames[i]
            );

            listModel.addElement(
                "Hospital Location: " + hospitalLocations[i]
            );

            listModel.addElement(
                "Years Since Inspection: "
                + inspectionYears[i] + " Years"
            );

            listModel.addElement(
                "----------------------------------------"
            );
        }
    }

    // Clear input controls and displayed inspection list
    private void clearControls() {

        txtHospitalName.setText("");
        txtHospitalLocation.setText("");

        cmbYears.setSelectedIndex(0);

        listModel.clear();

        txtHospitalName.requestFocusInWindow();
    }

    // Main method: application starting point
    public static void main(String[] args) {

        SwingUtilities.invokeLater(() -> {

            HospitalInspections form =
                new HospitalInspections();

            form.setVisible(
public class Product {

    // Variables needed
    private String[] productNames;
    private int[] productsSold;
    private int count;

    // Constructor
    public Product() {
        productNames = new String[10];
        productsSold = new int[10];
        count = 0;
    }

    // Method to add product details
    public void AddProduct(String name, int quantity) {
 
If method
        if (count < 10) {
            productNames[count] = name;
            productsSold[count] = quantity;
            count++;
        }
    }

    // Calculate total products sold
    public int GetTotalProductsSold() {

        int total = 0;

        for (int i = 0; i < count; i++) {
            total += productsSold[i];
        }

        return total;
    }

    // Calculate average products sold
    public double GetAverageProductSold() {

        if (count == 0) {
            return 0;
        }

        return (double) GetTotalProductsSold() / count;
    }

    // Find the most popular product
    public String GetMostPopularProduct() {

        if (count == 0) {
            return "No products available";
        }

        int highest = productsSold[0];
        int position = 0;

        for (int i = 1; i < count; i++) {

            if (productsSold[i] > highest) {
                highest = productsSold[i];
                position = i;
            }
        }

        return productNames[position];
    }
}
Question 2
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class ProductApp extends JFrame {

    // Declare variables
    private JTextField txtCustomerName;
    private JTextField txtPrice;
    private JComboBox<String> cmbProduct;
    private JTextArea txtReport;
    private JButton btnProcess;

    // Constructor
    public ProductApp() {

        setTitle("Product App");
        setSize(550, 550);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        // Create menu bar
        JMenuBar menuBar = new JMenuBar();

        JMenu fileMenu = new JMenu("File");
        JMenu editMenu = new JMenu("Edit");

        JMenuItem exitItem = new JMenuItem("Exit");
        JMenuItem clearItem = new JMenuItem("Clear");

        fileMenu.add(exitItem);
        editMenu.add(clearItem);

        menuBar.add(fileMenu);
        menuBar.add(editMenu);

        setJMenuBar(menuBar);

        // Create main panel
        JPanel panel = new JPanel();
        panel.setLayout(new GridLayout(5, 2, 10, 15));

        panel.setBorder(
            BorderFactory.createEmptyBorder(20, 20, 20, 20)
        );

        // Name of the customer
        panel.add(new JLabel("Customer Name:"));

        txtCustomerName = new JTextField();
        panel.add(txtCustomerName);

        // Product selection
        panel.add(new JLabel("Select Product:"));

        String[] products = {
            "Cozy Nights Monarch"
        };

        cmbProduct = new JComboBox<>(products);
        panel.add(cmbProduct);

        // Product price
        panel.add(new JLabel("Enter Price:"));

        txtPrice = new JTextField();
        panel.add(txtPrice);

        // Processing
        btnProcess = new JButton("PROCESS");

        panel.add(new JLabel(""));
        panel.add(btnProcess);

        // Enter the area
        txtReport = new JTextArea();
        txtReport.setEditable(false);

        JScrollPane scrollPane =
            new JScrollPane(txtReport);

        add(panel, BorderLayout.NORTH);
        add(scrollPane, BorderLayout.CENTER);

        // Button event
        btnProcess.addActionListener(e -> processSale());

        // Menu events
        exitItem.addActionListener(e -> System.exit(0));

        clearItem.addActionListener(e -> clearFields());
    }

    // Process sales information
    private void processSale() {

        try {

            // Get customer information
            String customerName =
                txtCustomerName.getText();

            String productName =
                (String) cmbProduct.getSelectedItem();

            double price =
                Double.parseDouble(txtPrice.getText());

            // Validate the informs needed
            if (customerName.trim().isEmpty() || price <= 0) {

                JOptionPane.showMessageDialog(
                    this,
                    "Please enter valid customer details and price."
                );

                return;
            }

            // Calculate VAT
            double vat = price * 0.15;

            // Calculate commission
            double commission = price * 0.05;

            // Calculate total sale amount
            double total = price + vat + commission;

            // Display report
            txtReport.setText(
                "========== PRODUCT SALES REPORT ==========\n\n"
                + "Customer Name: " + customerName + "\n"
                + "Product Name: " + productName + "\n"
                + "Product Price: R" + String.format("%.2f", price) + "\n"
                + "VAT Amount: R" + String.format("%.2f", vat) + "\n"
                + "Commission Amount: R"
                + String.format("%.2f", commission) + "\n"
                + "Total Sale Amount: R"
                + String.format("%.2f", total)
                + "\n\n=========================================="
            );

        } catch (NumberFormatException e) {

            JOptionPane.showMessageDialog(
                this,
                "Please enter a valid numerical price.",
                "Input Error",
                JOptionPane.ERROR_MESSAGE
            );
        }
    }

    // Clear all input fields
    private void clearFields() {

        txtCustomerName.setText("");
        txtPrice.setText("");
        cmbProduct.setSelectedIndex(0);
        txtReport.setText("");
    }

    // Main method
    public static void main(String[] args) {

        SwingUtilities.invokeLater(() -> {

            ProductApp app = new ProductApp();

            app.setVisible(true);
        });
    }
}

public interface IProductCalculations {
    double GetVat();
    double GetCommission();
    double GetTotal();
}

public class ProductCalculations implements IProductCalculations {
    private double salesAmount;
    private double vatRate;        // e.g., 0.15 for 15% VAT
    private double commissionRate; // e.g., 0.05 for 5% commission

    // Constructor to initialize sales and rates
    public ProductCalculations(double salesAmount, double vatRate, double commissionRate) {
        this.salesAmount = salesAmount;
        this.vatRate = vatRate;
        this.commissionRate = commissionRate;
    }

    @Override
    public double GetVat() {
        return salesAmount * vatRate;
    }

    @Override
    public double GetCommission() {
        return salesAmount * commissionRate;
    }

    @Override
    public double GetTotal() {
        // Total sale amount including VAT
        return salesAmount + GetVat();
    }
}

import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;

public class ProductCalculationsTests {

    @Test
    public void GetVat_WithValidData_ReturnsCorrectValue() {
        // Arrange: Set up test data with a known sales amount and VAT rate
        double salesAmount = 1000.0;
        double expectedVat = 150.0; // 1000.0 * 0.15 (15% VAT)
        
        IProductCalculations calculations = new ProductCalculations(salesAmount, 0.15, 0.05);

        // Act: Invoke the GetVat method
        double actualVat = calculations.GetVat();

        // Assert: Verify that the returned VAT matches the expected value
        assertEquals(expectedVat, actualVat, 0.001, "The GetVat method in the ProductCalculations class should correctly return the VAT amount[span_4](start_span)[span_4](end_span).");
    }
}

import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;

public class ProductCalculationsTests {

    @Test
    public void GetVat_WithValidData_ReturnsCorrectValue() {
        // Arrange: Set up test data with a known sales amount and VAT rate
        double salesAmount = 1000.0;
        double expectedVat = 150.0; // 1000.0 * 0.15 (15% VAT)
        
        IProductCalculations calculations = new ProductCalculations(salesAmount, 0.15, 0.05);

        // Act: Invoke the GetVat method
        double actualVat = calculations.GetVat();

        // Assert: Verify that the returned VAT matches the expected value
        assertEquals(expectedVat, actualVat, 0.001, "The GetVat method in the ProductCalculations class should correctly return the VAT amount[span_4](start_span)[span_4](end_span).");
    }
}

import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;

public class ProductCalculationsTests {

    }
}

public class ProductCalculations implements IProductCalculations {
    private double salesAmount;
    private double vatRate;        // e.g., 0.15 for 15% VAT
    private double commissionRate; // e.g., 0.05 for 5% commission

    // Constructor to initialize sales and rates
    public ProductCalculations(double salesAmount, double vatRate, double commissionRate) {
        this.salesAmount = salesAmount;
        this.vatRate = vatRate;
        this.commissionRate = commissionRate;
    }
//override method
    @Override
    public double GetVat() {
        return salesAmount * vatRate;
    }

    @Override
    public double GetCommission() {
        return salesAmount * commissionRate;
    }

    @Override
    public double GetTotal() {
        // Total sale amount including VAT
        return salesAmount + GetVat();
    }
}




}
	◦	
