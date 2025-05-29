```
get_host(Client)
```

Returns the host URL of a `Client` for connection to a `QPU` service.  

# Example

```jldoctest
julia> c = Client(
            host = "http://example.anyonsys.com",
            user = "test_user",
            access_token = "not_a_real_access_token"
        );

julia> get_host(c)
"http://example.anyonsys.com"

```
