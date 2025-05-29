firebase_fetchproviders(email="")

Fetch providers for email You can look all providers associated with a specified email by  issuing an HTTP POST request to the Auth createAuthUri endpoint.

# Example

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
