```
signup(db::Surreal; user::String, pass::String)::Union{String, Nothing}
Signs this connection up to a specific authentication scope.
```

#Arguments

  * `user`: username in signup query
  * `pass`: password in signup query

# Examples

```jldoctest
julia> signup(db, user="bob", pass="123456")
```
