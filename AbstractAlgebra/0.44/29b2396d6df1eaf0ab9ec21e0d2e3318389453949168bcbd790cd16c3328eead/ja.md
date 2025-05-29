```
gram(x::MatElem)
```

$$
x
$$

のグラム行列を返します。すなわち、$x$が$r\times c$行列である場合、$i$-行目と$j$-行目のドット積である$r\times r$行列を返します。

# 例

```jldoctest
julia> R, t = polynomial_ring(QQ, :t)
(Univariate polynomial ring in t over rationals, t)

julia> S = matrix_space(R, 3, 3)
Matrix space of 3 rows and 3 columns
  over univariate polynomial ring in t over rationals

julia> A = S([t + 1 t R(1); t^2 t t; R(-2) t + 2 t^2 + t + 1])
[t + 1       t             1]
[  t^2       t             t]
[   -2   t + 2   t^2 + t + 1]

julia> B = gram(A)
[2*t^2 + 2*t + 2   t^3 + 2*t^2 + t                   2*t^2 + t - 1]
[t^3 + 2*t^2 + t       t^4 + 2*t^2                       t^3 + 3*t]
[  2*t^2 + t - 1         t^3 + 3*t   t^4 + 2*t^3 + 4*t^2 + 6*t + 9]

```
