firebase*verifyemail(firebase*id*token=FIREBASE*ID_TOKEN)

Send email verification You can send an email verification for the current user by issuing an HTTP POST request to the Auth getOobConfirmationCode endpoint.

# Example

```julia
data = firebase_signin("ab669522@gmail.com","helloworld!!")
firebase_verifyemail((data["idToken"])
```
