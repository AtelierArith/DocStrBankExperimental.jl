```
group_indices(x) -> Dict
```

Computes the indices of elements in the vector `x` for each distinct value contained.  This information is useful for resampling strategies, such as stratified sampling.

See also [`group_counts`](@ref).

# Examples

```jldoctest
julia> x = [:yes, :no, :maybe, :yes];

julia> group_indices(x)
Dict{Symbol, Vector{Int64}} with 3 entries:
  :yes   => [1, 4]
  :maybe => [3]
  :no    => [2]
```
