```
(headers, queries, basicauth)
```

Provides:

  * `headers::NamedTuple` All request headers
  * `queries::NamedTuple` All request query parameters
  * `basicauth::Function` returns NamedTuple(username, password) if found, or `nothing`

`basicauth` will first look for basicauth details in the headers, then the parameters, returning the first one found or `nothing`

Optionally, `basicauth` can be passed two parameters:

`basicauth([usernamekey::String, passwordkey::String])`

which define which query parameters to look up. Defaults to `("username","password")`.

# Example:

```julia
function authfunction(details::RequestDetails)
    headers = details.headers
    queries = details.queries
    auth = details.basicauth()

    auth !== nothing && return auth.username === username && auth.password === password
    return false 
end
```
