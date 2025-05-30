```
Array(A::MatrixElem{T}) where T <: NCRingElement
```

同じ要素を持つ同じ次元のJulia `Matrix` に `A` を変換します。

# 例

```jldoctest; setup = :(using AbstractAlgebra)
julia> R, x = ZZ["x"]; A = R[x^0 x^1; x^2 x^3]
[  1     x]
[x^2   x^3]

julia> Array(A)
2×2 Matrix{AbstractAlgebra.Generic.Poly{BigInt}}:
 1    x
 x^2  x^3
```
