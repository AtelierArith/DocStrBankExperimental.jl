```
list_discs(A::AbstractMatrix)
```

Compute the Gershgorin discs for a square matrix.

Each disc has its center at a diagonal element, and its radius is the smaller value between the row and column sums for that element.

# Arguments

  * `A::AbstractMatrix`: a square matrix (either real or complex).

## Examples

```jldoctest
julia> A = [4.0 1.0; 0.5 3.0]
2×2 Matrix{Float64}:
 4.0  1.0
 0.5  3.0

julia> list_discs(A)
2-element Vector{GershgorinDisc{Float64}}:
 GershgorinDisc{Float64}((4.0, 0.0), 0.5)
 GershgorinDisc{Float64}((3.0, 0.0), 0.5)
```
