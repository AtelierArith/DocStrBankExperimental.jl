```
minimal_polynomial(Lf::ZZLatWithIsom) -> QQPolyRingElem
```

Given a lattice with isometry $(L, f)$, return the minimal polynomial of the underlying isometry $f$.

# Examples

```jldoctest
julia> L = root_lattice(:A, 5);

julia> Lf = integer_lattice_with_isometry(L; neg=true);

julia> minimal_polynomial(Lf)
x + 1
```
