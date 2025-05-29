```
basis(L::SimpleNumField) -> Vector{NumFieldElem}
```

Return the canonical basis of a simple extension $L/K$, that is, the elements $1,a,\dotsc,a^{d - 1}$, where $d$ is the degree of $K$ and $a$ the primitive element.

# Examples

```jldoctest
julia> Qx, x = QQ["x"];

julia> K, a = number_field(x^2 - 2, "a");

julia> basis(K)
2-element Vector{AbsSimpleNumFieldElem}:
 1
 a
```
