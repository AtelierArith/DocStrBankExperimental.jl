realdb_get(url; query = Dict())

GET request to an endpoint.

# Example

```julia
realdb_init("https://[PROJECT_ID].asia-southeast1.firebasedatabase.app")
realdb_get("/users/jack/name")
```
