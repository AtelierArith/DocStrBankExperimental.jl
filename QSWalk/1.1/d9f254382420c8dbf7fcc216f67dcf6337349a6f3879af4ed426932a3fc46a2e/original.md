```
res(matrix)
```

Return vectorization of the `matrix` in the row order. This is equivalent to `Base.vec(transpose(matrix))`.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> M = reshape(1:9, (3, 3))'*1im
3×3 Array{Complex{Int64},2}:
 0+1im  0+2im  0+3im
 0+4im  0+5im  0+6im
 0+7im  0+8im  0+9im

julia> v = res(M)
9-element reshape(::LinearAlgebra.Transpose{Complex{Int64},Array{Complex{Int64},2}}, 9) with eltype Complex{Int64}:
 0 + 1im
 0 + 2im
 0 + 3im
 0 + 4im
 0 + 5im
 0 + 6im
 0 + 7im
 0 + 8im
 0 + 9im

julia> res(unres(v)) == v
true
```
