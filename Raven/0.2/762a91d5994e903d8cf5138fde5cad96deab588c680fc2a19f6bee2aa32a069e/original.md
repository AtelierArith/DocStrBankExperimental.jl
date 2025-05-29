```
unflatten(T::Type, data, use::Type=Real)
```

Construct an object from Tuple or Vector `data` and a Type `T`. The `data` should be at least as long as the queried fields (of type `use`) in `T`.

# Examples

```julia
julia> unflatten(Tuple{Tuple{Int,Int},Complex{Int,Int}}, (1, 2, 3, 4))
((1, 2), 3 + 4im)

```
