realdb*put(url, body = Dict("name"=> "real*db_test"); query = Dict())

`PUT` request to a endpoint.

# Example

```julia
realdb_init("https://[PROJECT_ID].asia-southeast1.firebasedatabase.app")
body = Dict("first"=>"Ash", "last"=>"Sparrow")
realdb_put("/users/jack/name",body)
```
