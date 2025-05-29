```
*(P::Perm, x::MatrixElem{T}) where T <: NCRingElement
```

行列 $x$ の行に対して置換 $P$ を適用し、結果を返します。

# 例

```jldoctest
julia> R, t = polynomial_ring(QQ, :t)
(Univariate polynomial ring in t over rationals, t)

julia> S = matrix_space(R, 3, 3)
Matrix space of 3 rows and 3 columns
  over univariate polynomial ring in t over rationals

julia> G = SymmetricGroup(3)
Full symmetric group over 3 elements

julia> A = S([t + 1 t R(1); t^2 t t; R(-2) t + 2 t^2 + t + 1])
[t + 1       t             1]
[  t^2       t             t]
[   -2   t + 2   t^2 + t + 1]

julia> P = G([1, 3, 2])
(2,3)

julia> B = P*A
[t + 1       t             1]
[   -2   t + 2   t^2 + t + 1]
[  t^2       t             t]

```
