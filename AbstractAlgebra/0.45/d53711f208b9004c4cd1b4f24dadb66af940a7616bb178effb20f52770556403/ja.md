```
det(M::MatrixElem{T}) where {T <: RingElement}
```

行列 $M$ の行列式を返します。$M$ が正方行列であると仮定します。

# 例

```jldoctest
julia> R, x = polynomial_ring(QQ, :x)
(Univariate polynomial ring in x over rationals, x)

julia> A = R[x 1; 1 x^2];

julia> d = det(A)
x^3 - 1
```
