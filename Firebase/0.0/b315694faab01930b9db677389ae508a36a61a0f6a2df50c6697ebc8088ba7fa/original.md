firebase*changeemail(newemail="",firebase*id*token=  FIREBASE*ID_TOKEN)

Change email You can change a user's email by issuing an  HTTP POST request to the Auth setAccountInfo endpoint.

# Example

`julia data = firebase_signin("ab669522@gmail.com,"helloworld!!") firebase_changeemail("ab6695221@gmail.com",data["idToken"]) data = firebase_signin("ab6695221@gmail.com,"helloworld!!") firebase_changeemail("ab669522@gmail.com",data["idToken"])``
