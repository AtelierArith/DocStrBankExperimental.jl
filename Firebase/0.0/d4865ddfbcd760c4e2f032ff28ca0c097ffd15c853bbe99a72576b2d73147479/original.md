firebase*deleteuser(firebase*id*token=FIREBASE*ID_TOKEN)

Delete account You can delete a current user by issuing an HTTP POST request to the Auth deleteAccount endpoint.

# Example

```julia
data = firebase_signup("ashwani121231@gmail.com","hello!!123")
firebase_deleteuser(data["idToken"])
```
