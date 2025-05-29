```
one(a)
```

Return the multiplicative identity in the algebraic structure of $a$, which can be either an element or parent.

# Examples

```jldoctest
julia> S = matrix_space(ZZ, 2, 2)
Matrix space of 2 rows and 2 columns
  over integers

julia> one(S)
[1   0]
[0   1]

julia> R, x = puiseux_series_field(QQ, 4, :x)
(Puiseux series field in x over rationals, x + O(x^5))

julia> one(x)
1 + O(x^4)

julia> G = GF(5)
Finite field F_5

julia> one(G)
1
```
