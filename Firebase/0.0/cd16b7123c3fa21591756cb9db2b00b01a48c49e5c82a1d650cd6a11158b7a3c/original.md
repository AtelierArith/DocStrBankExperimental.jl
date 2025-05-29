Link with email/password You can link an email/password to a current user by issuing an  HTTP POST request to the Auth setAccountInfo endpoint.

# Example

```julia
data = firebase_signin("ab669522@gmail.com","helloworld!!")
firebase_linkuserinfo("ash@gmail.com", "hello!!123as",data["idToken"])
data = firebase_signin("ash@gmail.com", "hello!!123as")
firebase_linkuserinfo("ab669522@gmail.com","helloworld!!",data["idToken"])
```
