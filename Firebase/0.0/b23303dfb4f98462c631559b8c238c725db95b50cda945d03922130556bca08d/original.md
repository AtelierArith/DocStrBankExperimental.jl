realdb*patch(url, body = Dict("name"=> "real*db_test"); query = Dict())

`PATCH` request to an endpoint.

# Example

```julia
realdb_init("https://[PROJECT_ID].asia-southeast1.firebasedatabase.app")
body =Dict("last"=>"Jones")
realdb_patch("/users/jack/name/",body)
```
