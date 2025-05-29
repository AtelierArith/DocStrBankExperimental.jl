```
charpoly(Y::MatrixElem{T}) where {T <: RingElement}
charpoly(S::PolyRing{T}, Y::MatrixElem{T}) where {T <: RingElement}
```

平方行列 $Y$ の特性多項式 $p$ を返します。$Y$ と同じ基底環上の多項式環 $S$ が供給されると、結果の多項式はそれの要素となります。

# 例

```jldoctest
julia> R, = residue_ring(ZZ, 7);

julia> S = matrix_space(R, 4, 4)
Matrix space of 4 rows and 4 columns
  over residue ring of integers modulo 7

julia> T, y = polynomial_ring(R, :y)
(Univariate polynomial ring in y over R, y)

julia> M = S([R(1) R(2) R(4) R(3); R(2) R(5) R(1) R(0);
              R(6) R(1) R(3) R(2); R(1) R(1) R(3) R(5)])
[1   2   4   3]
[2   5   1   0]
[6   1   3   2]
[1   1   3   5]

julia> A = charpoly(T, M)
y^4 + 2*y^2 + 6*y + 2

julia> A = charpoly(M)
x^4 + 2*x^2 + 6*x + 2
```
