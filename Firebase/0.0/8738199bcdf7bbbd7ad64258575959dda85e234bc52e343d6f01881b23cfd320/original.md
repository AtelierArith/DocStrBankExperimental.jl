firebase*getuserinfo(firebase*id*token=FIREBASE*ID_TOKEN)

Get user data You can get a user's data by issuing an HTTP POST request to the Auth getAccountInfo endpoint.

# Example

```julia
data = firebase_signin("ab669522@gmail.com","helloworld!!")
firebase_getuserinfo(data["idToken"])
```
