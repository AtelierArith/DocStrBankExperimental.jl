```
Array(A::MatrixElem{T}) where T <: NCRingElement
```

Convert `A` to a Julia `Matrix` of the same dimensions with the same elements.

# Examples

```jldoctest; setup = :(using AbstractAlgebra)
julia> R, x = ZZ["x"]; A = R[x^0 x^1; x^2 x^3]
[  1     x]
[x^2   x^3]

julia> Array(A)
2×2 Matrix{AbstractAlgebra.Generic.Poly{BigInt}}:
 1    x
 x^2  x^3
```
