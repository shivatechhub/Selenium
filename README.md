# Selenium

Selenium is an open-source suite of tools used for automating web browsers. It allows developers to write scripts in various programming languages (such as Java, Python, C#, Ruby, and JavaScript) to automate the process of interacting with a website. This can include tasks like testing web applications, scraping data from websites, or automating repetitive tasks in a web browser.


Here are the key components and features of Selenium:
### **1. Selenium WebDriver**

- It is the core component of Selenium that allows for interaction with web browsers. <br>
- It provides a programming interface to control and interact with a browser, simulating user actions such as clicking buttons, typing text into fields, and navigating between pages. <br>
- Supports multiple browsers, including Chrome, Firefox, Safari, and Edge. <br>
- WebDriver interacts directly with the browser (unlike Selenium RC, which used a JavaScript-based approach). <br>


### **2. Selenium Grid**

- Selenium Grid allows you to run tests in parallel across multiple machines and browsers, speeding up test execution and enabling cross-browser testing. <br>
- It works by creating a hub (central server) that controls different nodes (machines with different browsers). <br>


### **3. Selenium IDE (Integrated Development Environment)**

- Selenium IDE is a browser extension for Firefox and Chrome that allows for the recording and playback of tests. It is especially useful for those who are new to Selenium or need a quick way to create basic tests without writing code. <br>
- It provides a simple interface to record actions, like clicking buttons and entering text, then automatically generates the corresponding code for those actions. <br>

### **4. Selenium RC (Remote Control**

- Selenium RC was an earlier version of Selenium that allowed automation of web browsers by injecting JavaScript code into the page.
- However, Selenium RC is now considered outdated and is replaced by WebDriver, which is faster, more stable, and more flexible.

### Key Features of Selenium:
- Cross-Browser Compatibility: Selenium supports a wide range of browsers, allowing tests to be executed across different environments. <br>
- Cross-Platform Support: It works on different operating systems, including Windows, macOS, and Linux. <br>
- Language Support: It supports multiple programming languages like Java, Python, C#, JavaScript, Ruby, and Kotlin. <br>
- Headless Testing: Selenium allows for testing in headless mode (i.e., without a visible browser interface), which is useful for CI/CD pipelines or automated testing environments. <br>
- Framework Integration: Selenium can be integrated with various testing frameworks like TestNG, JUnit, and others, enabling robust and maintainable testing. <br>


### Common Use Cases:
- **Automated Web Testing:** Selenium is widely used for automated functional testing of web applications to ensure they perform as expected across different browsers. <br>
- **Web Scraping:** Automating the extraction of data from websites, particularly when data is dynamically generated (e.g., JavaScript-heavy websites). <br>
- **Regression Testing:** Selenium helps run tests automatically to verify that new changes or features haven't broken existing functionality. <br>


## **Steps to Set Up Selenium with Java:**
### **1. Set up Java Development Environment**
Make sure you have Java installed on your machine. You can download Java from Oracle's website.
You can check if Java is installed by running this command in the terminal or command prompt:
```
$ java -version
```


### **2. Install an Integrated Development Environment (IDE)**
You can use Eclipse, IntelliJ IDEA, or NetBeans to write your Selenium Java code. Eclipse is the most commonly used IDE for Selenium projects.
Download Eclipse from [here](https://www.eclipse.org/downloads/ "here").

### **3. Add Selenium WebDriver Dependency**
You need to add the Selenium WebDriver libraries to your project. There are two ways to do this:

**Option 1: Use Maven**
If you're using Maven, create a pom.xml file and add the following dependency:
```
<dependencies>
    <dependency>
        <groupId>org.seleniumhq.selenium</groupId>
        <artifactId>selenium-java</artifactId>
        <version>4.6.0</version>
    </dependency>
</dependencies>
```

Then, Maven will download the required libraries.


**4. Set Up WebDriver**
- You need a WebDriver to interact with the browser. For example, if you're using Chrome, you'll need the ChromeDriver.
- Download the appropriate WebDriver for your browser. For Chrome, get ChromeDriver from [here](https://googlechromelabs.github.io/chrome-for-testing/ "here").
- Make sure the WebDriver executable is in your system’s PATH or specify its location in your code.

### **Example:**
```
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class SeleniumTest {

    public static void main(String[] args) {
        // Set the path to the ChromeDriver executable (update the path as needed)
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");

        // Initialize the ChromeDriver
        WebDriver driver = new ChromeDriver();

        try {
            // Navigate to a webpage (e.g., Google)
            driver.get("https://www.google.com");

            // Get the title of the page
            System.out.println("Page title is: " + driver.getTitle());

            // Perform other interactions (optional)
            // Example: driver.findElement(By.name("q")).sendKeys("Selenium WebDriver");

        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Close the browser after use
            driver.quit();
        }
    }
}

```


## Selenium Webdriver Commands
**1. Initialize a Webdriver** : 
```
Webdriver driver = new ChromeDriver();
Webdriver driver = new FirefoxDriver();
Webdriver driver = new EdgeDriver();
```

**2. Opening a Website** :
Use the get() method to navigate to a URL.
```
driver.get("https://www.example.com");
```

**3. Maximizing the Window**
To maximize the browser window, use the manage().window().maximize() method.
```
driver.manage().window().maximize();
```

**4. Finding Web Elements**
WebDriver provides several methods for locating elements on a page. Common methods include findElement() and findElements(). Here are some examples:

```
By ID:
WebElement element = driver.findElement(By.id("elementId"));
```
```
By Name:
WebElement element = driver.findElement(By.name("elementName"));
```
```
By XPath:
WebElement element = driver.findElement(By.xpath("//button[@class='submit']"));
```
```
By CSS Selector:
WebElement element = driver.findElement(By.cssSelector(".className"));
```

**5. Clicking an Element**
You can perform a click action using the click() method.
```
WebElement button = driver.findElement(By.id("submitButton"));
button.click();
```

**6. Sending Keyboard Inputs**
To simulate typing into a text field, use the sendKeys() method.
```
WebElement textField = driver.findElement(By.id("username"));
textField.sendKeys("myUsername");
```

**7. Getting Text from an Element**
Use getText() to retrieve the text of an element.
```
WebElement message = driver.findElement(By.id("message"));
String text = message.getText();
System.out.println("Message: " + text);
```

**8. Handling Alerts**
WebDriver can handle JavaScript alerts using Alert interface.
**Accepting an Alert:**
```
Alert alert = driver.switchTo().alert();
alert.accept();
```

**Dismissing an Alert:**
```
Alert alert = driver.switchTo().alert();
alert.dismiss();
```

**Getting Alert Text:**
```
Alert alert = driver.switchTo().alert();
String alertText = alert.getText();
System.out.println("Alert text: " + alertText);
```
**9. Switching Between Frames**
You can switch to an iframe using switchTo().frame().
```
driver.switchTo().frame("frameName");
```
**Switching Back to Main Content:**
```
driver.switchTo().defaultContent();
```

**10. Scrolling the Page**
To scroll the page, you can execute JavaScript using JavascriptExecutor.
```
JavascriptExecutor js = (JavascriptExecutor) driver;
js.executeScript("window.scrollBy(0, 250)", "");
```


**11. Handling Multiple Windows/Tabs**
Switch between windows or tabs using the window handles.
```
String mainWindow = driver.getWindowHandle();
// Perform actions that open a new window/tab
Set<String> allWindows = driver.getWindowHandles();
for (String window : allWindows) {
    if (!window.equals(mainWindow)) {
        driver.switchTo().window(window);
        break;
    }
}
```

**12. Waiting for Elements**
There are two main types of waits: Implicit and Explicit.

**Implicit Wait:**
Implicit wait will make WebDriver wait for a certain amount of time before throwing an exception if the element is not found.
```
driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
```

**Explicit Wait:**
Explicit wait allows you to wait for a specific condition (like element visibility) before proceeding.
```
WebDriverWait wait = new WebDriverWait(driver, 10);
WebElement element = wait.until(ExpectedConditions.visibilityOfElementLocated(By.id("elementId")));
```

**13. Taking Screenshots**
You can capture a screenshot with TakesScreenshot interface.
```
File screenshot = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
FileUtils.copyFile(screenshot, new File("path/to/save/screenshot.png"));
```

**14. Closing the Browser**
Once you are done with the WebDriver, you should close the browser.
```
driver.quit(); // Closes all windows and ends the WebDriver session
driver.close(); // Closes the current browser window
```

**15. Getting the Current URL**
To get the URL of the current page:
```
String currentUrl = driver.getCurrentUrl();
System.out.println("Current URL: " + currentUrl);
```

**16. Handling Dropdowns**
You can select options from a dropdown using the Select class.
```
import org.openqa.selenium.support.ui.Select;
WebElement dropdown = driver.findElement(By.id("dropdown"));
Select select = new Select(dropdown);
select.selectByVisibleText("Option 1"); // Select option by visible text
select.selectByValue("optionValue"); // Select option by value
select.selectByIndex(2); // Select option by index
```


