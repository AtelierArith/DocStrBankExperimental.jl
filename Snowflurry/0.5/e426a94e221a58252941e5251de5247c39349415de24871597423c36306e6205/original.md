```
Client
```

A data structure that represents a *client* for connection to a QPU service.  

# Fields

  * `host::String` – URL of the QPU server.
  * `user::String` – Username.
  * `access_token::String` – User access token.
  * `realm::String` – Optional: Used to identify the host server realm for the submission of requests.

# Example

```jldoctest
julia> c = Client(
            host = "http://example.anyonsys.com",
            user = "test_user",
            access_token = "not_a_real_access_token",
            realm = "test_realm"
        )
Client for QPU service:
   host:         http://example.anyonsys.com
   user:         test_user 
   realm:        test_realm 
 
```
