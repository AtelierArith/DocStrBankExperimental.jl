firebase_fetchproviders(email="")

メールのプロバイダーを取得する 指定されたメールに関連付けられたすべてのプロバイダーを取得するには、Auth createAuthUriエンドポイントにHTTP POSTリクエストを発行します。

# 例

```julia
julia> firebase_fetchproviders("ashwani1@gmail.com")
#= 
Dict{String, Any} with 5 entries:
  "allProviders"  => Any["password"]
  "kind"          => "identitytoolkit#CreateAuthUriResponse"
  "sessionId"     => "k8iBdCSLEeAbhhgKz6E4PC-ltCs"
  "signinMethods" => Any["password"]
  "registered"    => true
=#
```
