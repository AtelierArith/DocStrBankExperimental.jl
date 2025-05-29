```julia
stepify(x::AbstractVector)
```

Duplicate every element of an array.

Together with `stepifyedges`, allows for convenient plotting of  a histogram of bin counts and bin edges as a stepped line.

### Examples

```julia
julia> stepify([1,3,2])
6-element Vector{Int64}:
 1
 1
 3
 3
 2
 2

julia> plot(stepifyedges(binedges), stepify(bincounts))
# Returns a stepped line plot of a histogram
```
