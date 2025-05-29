```
bra([T = Float64], i::Integer, d::Integer) -> SparseVector{Complex{T}}'
```

Create a dual vector representing the bra associated to `i`th computational basis vector in dimension `d`.

## Example

```jldoctest
julia> bra(1,2)
1×2 LinearAlgebra.Adjoint{Complex{Float64},SparseVector{Complex{Float64},Int64}}:
 1.0-0.0im  0.0-0.0im

julia> collect(ans)
1×2 Array{Complex{Float64},2}:
 1.0-0.0im  0.0-0.0im
```
