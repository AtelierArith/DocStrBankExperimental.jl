```
add_session_data(
    key::String,
    value::Union{String, Real}, 
    req::HTTP.Request = Genie.Requests.request(),
    res::HTTP.Response = Genie.Responses.getresponse()
)::Nothing
```

Add data to a session in the session storage.

# Arguments

  * `key`: the key of the data to be added.
  * `value`: the value of the data to be added.
  * `req`: the HTTP.Request object.
  * `res`: the HTTP.Response object.

# Return

The function returns nothing.
