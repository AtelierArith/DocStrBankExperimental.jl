```
minimal_polynomial(Lf::ZZLatWithIsom) -> QQPolyRingElem
```

与えられた格子 $(L, f)$ に対して、基礎となる同型 $f$ の最小多項式を返します。

# 例

```jldoctest
julia> L = root_lattice(:A, 5);

julia> Lf = integer_lattice_with_isometry(L; neg=true);

julia> minimal_polynomial(Lf)
x + 1
```
