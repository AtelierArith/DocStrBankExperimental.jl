firebase_signinanon(returnSecureToken::Bool= true)

Sign in anonymously You can sign in a user anonymously by issuing an HTTP POST request to the Auth signupNewUser endpoint.

# Exampleemail::String="", password::String="",

```julia
julia> firebase_signinanon()
#=
Dict{String, Any} with 5 entries:
  "refreshToken" => "AGEhc0DiE1zelLdCW2KG9wMRwZKcZI6EuSef4hsIc6uOZp0I3SYUTf0Hib_XgvtgY1yeqgFNqJ0…
  "kind"         => "identitytoolkit#SignupNewUserResponse"
  "localId"      => "3T8r7DD99zO9qKL1k56boC2iiXF2"
  "expiresIn"    => "3600"
  "idToken"      => "eyJhbGciOiJSUzI1NiIsImtpZCI6ImRjNGQwMGJjM2NiZWE4YjU0NTMzMWQxZjFjOTZmZDRlNjd…
=#
```
