```
AffineParametricArray{T, N, MT<:AbstractArray{T, N}}
```

Array whose elements have an affine dependency on a set of parameteres $p₁, p₂, …, pₙ$.

### Fields

  * coeffs::Vector{MT} – vector of arrays, corresponds to the coefficients of each variable.

### Example

```jldoctest
julia> @affinevars x y z
3-element Vector{AffineExpression{Int64}}:
 x
 y
 z

julia> A = AffineParametricArray([x+y x-1;x+y+z 1])
2×2 AffineParametricMatrix{Int64, Matrix{Int64}}:
 x+y    x-1
 x+y+z  1
```
