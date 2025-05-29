```
unsqueeze(; dims)
```

Returns a function which, acting on an array, inserts a dimension of size 1 at `dims`.

# Examples

```jldoctest
julia> rand(21, 22, 23) |> unsqueeze(dims=2) |> size
(21, 1, 22, 23)
```
