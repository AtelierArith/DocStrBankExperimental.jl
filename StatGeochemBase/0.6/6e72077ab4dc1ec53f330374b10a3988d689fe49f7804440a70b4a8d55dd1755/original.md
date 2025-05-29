```julia
stepifyedges(x::AbstractVector)
```

Duplicate every element of an array except for the first and last.

Together with `stepify`, allows for convenient plotting of  a histogram of bin counts and bin edges as a stepped line.

### Examples

```julia
julia> stepifyedges([1,2,3,4])
6-element Vector{Int64}:
 1
 2
 2
 3
 3
 4

julia> plot(stepifyedges(binedges), stepify(bincounts))
# Returns a stepped line plot of a histogram
```
