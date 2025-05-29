firebase_signup(email::String="", password::String="", returnSecureToken::Bool= true)

メール/パスワードでサインアップ 新しいメールとパスワードのユーザーを作成するには、AuthのsignupNewUserエンドポイントにHTTP POSTリクエストを発行します。

# 例

```julia
set_webapikey("WEB_API_KEY")
firebase_signup("ashwani@gmail.com","hello!!")
#=
Dict{String, Any} with 6 entries:
  "refreshToken" => "AGEhc0AjgXJevwy_rkJ3r4VUHc4EEORngVF-rwEtOuO007AymRqbAzVnn1iAMCZNHqzwnCI1X8fkJ0OPE2fTuGN7ameU6P7SmibwIFs8sOZxUI8C_uklOkk1IG5DFdWXAC45mK_0Hy4tuJXJUvI8Kuy6LS-GERZ5Bc…
  "kind"         => "identitytoolkit#SignupNewUserResponse"
  "localId"      => "GRCBj28Pkhat0mYsJS0BVrlVmJd2"
  "expiresIn"    => "3600"
  "idToken"      => "eyJhbGciOiJSUzI1NiIsImtpZCI6ImRjNGQwMGJjM2NiZWE4YjU0NTMzMWQxZjFjOTZmZDRlNjdjNTFlODkiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vZmlyLWp…
  "email"        => "ashwani@gmail.com"
=#
```
