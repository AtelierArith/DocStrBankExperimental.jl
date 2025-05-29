```
EmptySpatialField()
```

Create a blank spatial field. This is primarily useful for initializing a sum of spatial fields.

# Example

```jldoctest
julia> g = EmptySpatialField()
EmptySpatialField()

julia> g(2,3)
0.0
```
