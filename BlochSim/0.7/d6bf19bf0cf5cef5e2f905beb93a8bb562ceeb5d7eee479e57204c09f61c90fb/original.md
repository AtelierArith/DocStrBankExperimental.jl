```
BlochMcConnellMatrix(A)
BlochMcConnellMatrix{T}(N)
BlochMcConnellMatrix(N)
```

Create a `BlochMcConnellMatrix` object with `N` compartments and representing a fixed-size 3N×3N matrix.

# Properties

  * `A::NTuple{N,NTuple{N,BlochMatrix{<:Real}}}`: List of 3×3 matrices that comprise the blocks of the `BlochMcConnellMatrix`; `A[i][j]` is the (i,j)th block

# Examples

```jldoctest
julia> B = BlochMcConnellMatrix(3)
BlochMcConnellMatrix{Float64,3}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0

julia> fill!(B, 0.5)

julia> B
BlochMcConnellMatrix{Float64,3}:
 0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5
 0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5
 0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5
 0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5
 0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5
 0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5
 0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5
 0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5
 0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5  0.5
```
