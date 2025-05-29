```
gram(x::MatElem)
```

Return the Gram matrix of $x$, i.e. if $x$ is an $r\times c$ matrix return the $r\times r$ matrix whose entries $i, j$ are the dot products of the $i$-th and $j$-th rows, respectively.

# Examples

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
