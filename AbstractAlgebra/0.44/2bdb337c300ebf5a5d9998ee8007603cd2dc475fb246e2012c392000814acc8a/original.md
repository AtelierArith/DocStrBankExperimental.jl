```
zero(a)
```

Return the additive identity in the algebraic structure of $a$, which can be either an element or parent.

# Examples

```jldoctest
julia> S = matrix_ring(QQ, 2)
Matrix ring of degree 2
  over rationals

julia> zero(S)
[0//1   0//1]
[0//1   0//1]

julia> R, x = polynomial_ring(ZZ, :x)
(Univariate polynomial ring in x over integers, x)

julia> zero(x^3 + 2)
0
```
