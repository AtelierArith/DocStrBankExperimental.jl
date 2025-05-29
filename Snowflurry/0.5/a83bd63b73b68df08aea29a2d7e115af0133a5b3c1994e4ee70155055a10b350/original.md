```
get_excluded_positions(
    c::Union{LineConnectivity,LatticeConnectivity}
)::Vector{Tuple{Int, Int}}
```

Returns the list of `excluded_positions` for the connectivity.

# Example

```jldoctest
julia> get_excluded_positions(LatticeConnectivity(3, 4, [1, 3]))
2-element Vector{Int64}:
 1
 3

```
