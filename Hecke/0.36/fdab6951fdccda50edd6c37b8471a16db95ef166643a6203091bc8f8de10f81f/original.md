```
number_field(f::Vector{PolyRingElem{<:NumFieldElem}}, s::VarName="_\$", check = true)
                                          -> NumField, Vector{NumFieldElem}
```

Given a list $f_1, \ldots, f_n$ of univariate polynomials in $K[x]$ over some number field $K$, constructs the extension $K[x_1, \ldots, x_n]/(f_1(x_1), \ldots, f_n(x_n))$.

# Examples

```jldoctest
julia> Qx, x = QQ["x"];

julia> K, a = number_field([x^2 - 2, x^2 - 3], "a")
(Non-simple number field of degree 4 over QQ, AbsNonSimpleNumFieldElem[a1, a2])
```
