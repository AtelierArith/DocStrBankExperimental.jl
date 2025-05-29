```
basis(L::NonSimpleNumField) -> Vector{NumFieldElem}
```

Returns the canonical basis of a non-simple extension $L/K$. If $L = K(a_1,\dotsc,a_n)$ where each $a_i$ has degree $d_i$, then the basis will be $a_1^{i_1}\dotsm a_d^{i_d}$ with $0 \leq i_j \leq d_j - 1$ for $1 \leq j \leq n$.

# Examples

```jldoctest
julia> Qx, x = QQ["x"];

julia> K, (a1, a2) = number_field([x^2 - 2, x^2 - 3], "a");

julia> basis(K)
4-element Vector{AbsNonSimpleNumFieldElem}:
 1
 a1
 a2
 a1*a2
```
