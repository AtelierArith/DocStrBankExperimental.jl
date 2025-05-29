firebase*changepassword(newpassword="", firebase*id*token=FIREBASE*ID_TOKEN)

Change password You can change a user's password by issuing an  HTTP POST request to the Auth setAccountInfo endpoint.

# Example

`julia data = firebase_signin("ab669522@gmail.com","helloworld!!") firebase_changepassword("hellopaaji!!",data["idToken"]) data = firebase_signin("ab6695221@gmail.com","hellopaaji!!") firebase_changepassword("helloworld!!",data["idToken"])``
