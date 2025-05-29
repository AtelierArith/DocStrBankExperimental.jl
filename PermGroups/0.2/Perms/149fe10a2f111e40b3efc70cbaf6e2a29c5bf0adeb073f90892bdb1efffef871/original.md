`invpermute(m::AbstractMatrix,p::Perm;dims=1)`

invpermutes  by `p` the rows, columns or  both of the matrix `m` depending on the value of `dims`.

```julia-repl
julia> m=reshape(1:9,3,3)
3×3 reshape(::UnitRange{Int64}, 3, 3) with eltype Int64:
 1  4  7
 2  5  8
 3  6  9

julia> p=Perm(1,2,3)
(1,2,3)

julia> invpermute(m,p)
3×3 Matrix{Int64}:
 3  6  9
 1  4  7
 2  5  8

julia> invpermute(m,p;dims=2)
3×3 Matrix{Int64}:
 7  1  4
 8  2  5
 9  3  6

julia> invpermute(m,p;dims=(1,2))
3×3 Matrix{Int64}:
 9  3  6
 7  1  4
 8  2  5
```
