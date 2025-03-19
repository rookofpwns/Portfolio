# Coding Portfolio

## About Me
I am a software developer specializing in Rust, Python, and backend systems. My work involves building integrations between business applications.

---

## Selected Projects

### **1. Web Automation & Session Handling**
**Technologies:** Rust, WebDriver, reqwest

**Problem:** Pulling cookies with a user friendly approach to then automate tasks.

**Solution:** Built a Rust-based WebDriver integration that extracts session cookies and transfers them into a `reqwest` session for further authenticated requests. This provides a way for a user to login through a familiar interface and allow the application to call API's. This was very useful for specific Applications.

**Code Snippet:**
```rust
use fantoccini::{Client, Locator};
use reqwest::Client as ReqwestClient;

async fn extract_cookies() -> Result<(), Box<dyn std::error::Error>> {
    let client = Client::new("http://localhost:4444").await?;
    client.goto("https://example.com").await?;

    let cookies = client.get_cookies().await?;
    let session = ReqwestClient::builder()
        .cookie_store(true)
        .build()?;
    
    let api_call = session.get("https://api.example.com/)
      .send()
      .await()?;

    println!("Info: {:#?}", api_call)
    Ok(())
}
```


---

### **2. Update Database Through CSV**
**Technologies:** Python
**Problem:** The Enterprise Resource Planning (ERP) systems has an unintuitive mass update tool.

**Solution:** Created a program that allows users familiar with Excel to update assets, convient as the ERP gives users reports in a CSV format.

**Code Snippet:**
```python
# Main function, starts the process of locking the GUI, updating the GUI, and providing errors to the Error log.
 def csv_move(self):

      # Checks
      csv_file = self.primary.file_selected.get()
      if csv_file == '' or csv_file == None:
          self.windowStateChange(NORMAL)
          self.logs.logText.insert(
            "end",
            f"\nProgram Halted Early: No file selected. {self.erpObj.log_date()}"
            + "\n------------------End of Log------------------"
            )
          self.primary.display.configure(text=f"Please select a File!") 
          return
      
      self.erpObj.data = self.data2
      self.erpObj.read_csv()
      try:
          self.primary.display.configure(text="Working . . .")
          self.erpObj.update()
      except Exception as error:
          time.sleep(3)
          print(traceback.format_exc())
          self.windowStateChange(NORMAL)
          self.primary.display.configure(text="Error!")
          self.logs.logText.insert(
            "end",
            f"\nProgram Halted Early: {error} {self.erpObj.log_date()}"
            + "\n------------------End of Log------------------"
            )
          return
      
      self.primary.display.configure(text="Done!")
      self.primary.progress.set(1)
      time.sleep(5)
      self.primary.display.configure(text="Idle")

      # Resets all buttons to normal, currently if an error occurs, it locks all buttons.
      self.windowStateChange(NORMAL)
      self.logs.logText.insert("end","\n------------------End of Log------------------")
}
```
![image](https://github.com/user-attachments/assets/382e2ea0-adf1-4b5c-9f2c-cd68f1c6bc8e)![image](https://github.com/user-attachments/assets/ef36c489-8aca-4e35-8f77-d72de251a402)





---

### **3. API Development**
**Technologies:** Flask, CloudFlare Zero Trust

**Problem:** A Relatively new feature in Phonecheck is to test and return information on Macbooks. My current ERP system does not have native support to automatically pull the information.

**Solution:** I have made an API endpoint and User application to search for information on Phonecheck, then will upload it to our system. This also let me transform the data or split data into appropriate fields that would not normally be handled by our system.

**Code Snippet:**
```python
from flask import Flask, request, jsonify


@app.route('/phonecheck', methods= ['POST'])
def phonecheckMac():
  if request.method == 'POST';
    json_data= request.get_json()
  else:
    return jsonify({"httpStatusCode" : 405, "statusMessage": "Unauthorized"})

  if json_data['Authorization'] != "Bearer " + keys.secret_key:
    status = {"httpStatusCode" : 401, "statusMessage": "Unauthorized"}
    return jsonify(status)

  if "UID" in json_data.keys():
    try:
      data = ph.upload_erp(str(json_data['UID']))
      return jsonify(data)
    except Exception as e
      return jsonify({"httpStatusCode" : 400, "statusMessage": "Failed to upload", "error" : f"Error in API\n {e}"})
```

![image](https://github.com/user-attachments/assets/e5f0e98c-bf3a-4760-96bf-c1b82e6a7dd0)


---

## Skills & Technologies
- **Programming Languages:** Rust, Python, HTML, CSS
- **Frameworks & Libraries:** Flask, Requests, reqwest, Selenium
- **Specializations:** Web Automation, Business Integrations.

---

This portfolio is a glimpse into my technical expertise through problem-solving examples rather than full projects. Let’s build something great together!

