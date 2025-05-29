firebase_signinanon(returnSecureToken::Bool= true)

匿名でサインインする ユーザーを匿名でサインインさせるには、Auth signupNewUser エンドポイントに対して HTTP POST リクエストを発行します。

# 例email::String="", password::String="",

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
