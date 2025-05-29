プロバイダーのリンク解除 現在のユーザーからプロバイダーのリンクを解除するには、Auth setAccountInfo エンドポイントにHTTP POSTリクエストを発行します。

# 例

```julia
set_webapikey()

data = firebase_signup("ashwani12123@gmail.com","hello!!123")
#=
Dict{String, Any} with 6 entries:
  "refreshToken" => "AGEhc0A4Y-wFC0S2Cub-7TY2XNfZMYQf-YKzTdQWl9_SjrRpUW4d3QymQy5P1EN4Me8-SE695sPE_MBXoMoqTzKLy76nBvDGmybGmP4wnWLyrJql-HfoVPRtG1emeJ3E61DnDbUIZOvV-Y3GuzpJ57XZojHBM1aoMp…
  "kind"         => "identitytoolkit#SignupNewUserResponse"
  "localId"      => "neXn8Mg562VFgENRtA2SEC0NEBk1"
  "expiresIn"    => "3600"
  "idToken"      => "eyJhbGciOiJSUzI1NiIsImtpZCI6ImRjNGQwMGJjM2NiZWE4YjU0NTMzMWQxZjFjOTZmZDRlNjdjNTFlODkiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vZmlyLWp…
  "email"        => "ashwani12123@gmail.com"
=#
firebase_unlinkprovide(data["idToken"], "google.com")
#=
Dict{String, Any} with 6 entries:
  "kind"             => "identitytoolkit#SetAccountInfoResponse"
  "localId"          => "neXn8Mg562VFgENRtA2SEC0NEBk1"
  "passwordHash"     => "UkVEQUNURUQ="
  "emailVerified"    => false
  "providerUserInfo" => Any[Dict{String, Any}("rawId"=>"ashwani12123@gmail.com", "providerId"=>"password", "federatedId"=>"ashwani12123@gmail.com", "email"=>"ashwani12123@gmail.com")]
  "email"            => "ashwani12123@gmail.com"
=#
```
