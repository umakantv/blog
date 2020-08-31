# Callback Functions
In JavaScript, every variable is an object of its `class`, even functions you create are the objects of class `Function`.
And objects can be passed around as variables in other functions as `parameters`. And they can be called wherever necessary with the required parameters.  
This gives us a lot of advantage when creating `independent modules`. In open source community, when creating a tool for other developers, you sometimes have to provide a way for developers to integrate their code with your module.
 
## Example
Suppose you are creating a module that sends emails. Now if somebody is going to use this module in their code, they might want to know if the email went through or failed. They might want to take different actions in both the cases. For this purpose, you have to provide them a way to take the appropriate action.  
So what you can do is expect a function from them which define the necessary action depending on the values of your variables.



```javascript
class Transporter {
  constructor(email, password) {
    this.email = email;
    this.password = password;
  }
  sendMail(mailOptions, callback) {
    let error = null,
      result = "Mail sent.";
    // code to send email
    callback(error, result);
  }
}

const tp = new Transporter("johndoe@example.com", "password");

const mailOptions = {
  from: "johndoe <johndoe@example.com>",
  to: "foobar@example.com",
  text: "Hello"
};

tp.sendMail(mailOptions, (error, result) => {
  // this will be called after tp has done processing email request
  // it can either be successful, in which case error will be null
  // or it can fail, and error will not be null
  if (error) {
    // do something when email is not sent
  } else {
    // do something when email is sent
  }
});

```