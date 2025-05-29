```
characteristic_polynomial(Lf::ZZLatWithIsom) -> QQPolyRingElem
```

Given a lattice with isometry $(L, f)$, return the characteristic polynomial of the underlying isometry $f$.

# Examples

```jldoctest
julia> L = root_lattice(:A, 5);

julia> Lf = integer_lattice_with_isometry(L; neg=true);

julia> factor(characteristic_polynomial(Lf))
1 * (x + 1)^5
```
