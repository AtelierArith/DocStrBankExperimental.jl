```
ket([T = Float64], i::Integer, d::Integer) -> SparseVector{Complex{T}}
```

Create a vector representing the `i`th computational basis vector in dimension `d`.

## Example

```jldoctest
julia> ket(1,2)
2-element SparseVector{Complex{Float64},Int64} with 1 stored entry:
  [1]  =  1.0+0.0im

julia> collect(ans)
2-element Array{Complex{Float64},1}:
 1.0 + 0.0im
 0.0 + 0.0im
```
