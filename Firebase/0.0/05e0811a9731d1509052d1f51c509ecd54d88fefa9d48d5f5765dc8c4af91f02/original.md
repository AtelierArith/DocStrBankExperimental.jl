firebase_signin(email::String="data", password::String="data", returnSecureToken::Bool= true)

Sign in with email / password You can sign in a user with an email and password by issuing an HTTP POST request to the Auth verifyPassword endpoint.

# Example

```julia
firebase_signin("ashwani1@gmail.com" , "hello1231!!")
#=
Dict{String, Any} with 8 entries:
  "refreshToken" => "AGEhc0C1F9smilhBPdT5TYClumCwdzGI9q43s5r-MsqW-bJTeiIw1doG7zRF_VMX2a0WELR3zRB…
  "kind"         => "identitytoolkit#VerifyPasswordResponse"
  "localId"      => "zgrI4g3ualVJW7IEiRlPFg5jItA2"
  "displayName"  => ""
  "idToken"      => "eyJhbGciOiJSUzI1NiIsImtpZCI6ImRjNGQwMGJjM2NiZWE4YjU0NTMzMWQxZjFjOTZmZDRlNjd…
  "registered"   => true
  "expiresIn"    => "3600"
  "email"        => "ashwani1@gmail.com"
=#
```
