```
minpoly(M::MatElem{T}) where {T <: RingElement}
minpoly(S::PolyRing{T}, M::MatElem{T}) where {T <: RingElement}
```

平方行列 $M$ の最小多項式 $p$ を返します。同じ基底環上の多項式環 $S$ が供給されると、結果の多項式はそれの要素になります。

# 例

```jldoctest
julia> R = GF(13)
有限体 F_13

julia> S, y = polynomial_ring(R, :y)
R 上の y に関する単変数多項式環 (Univariate polynomial ring in y over R, y)

julia> M = R[7 6 1;
             7 7 5;
             8 12 5]
[7    6   1]
[7    7   5]
[8   12   5]

julia> A = minpoly(S, M)
y^2 + 10*y

julia> A = minpoly(M)
x^2 + 10*x

```
