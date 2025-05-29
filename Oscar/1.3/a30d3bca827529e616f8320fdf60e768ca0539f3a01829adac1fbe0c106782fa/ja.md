```
characteristic_polynomial(Lf::ZZLatWithIsom) -> QQPolyRingElem
```

与えられた同型 $(L, f)$ を持つ格子に対して、基礎となる同型 $f$ の特性多項式を返します。

# 例

```jldoctest
julia> L = root_lattice(:A, 5);

julia> Lf = integer_lattice_with_isometry(L; neg=true);

julia> factor(characteristic_polynomial(Lf))
1 * (x + 1)^5
```
