```
DeltaArray(V::AbstractVector)
```

Construct a matrix with `V` as its diagonal.

See also [`delta`](@ref).

# Examples

```jldoctest
julia> DeltaArray([1, 10, 100])
3×3 DeltaArray{Int64, 2, Vector{Int64}}:
 1   0    0
 0  10    0
 0   0  100
```
