```
get_session_data(
    key::String,
    req::HTTP.Request = Genie.Requests.request(),
    res::HTTP.Response = Genie.Responses.getresponse()
)::Union{Any, Nothing}
```

Gets the data for a session in the session store that matches the key.

# Arguments

  * `key`: the key of the data to be retrieved.
  * `req`: the HTTP.Request object. By default is Genie.Requests.request().
  * `res`: the HTTP.Response object. By default is Genie.Responses.getresponse().

# Return

The function returns the data if it exists, otherwise it returns nothing.
