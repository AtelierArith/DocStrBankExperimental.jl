```
lattice(V::AbstractSpace, B::PMat ; check::Bool = true) -> AbstractLat
```

Given an ambient space `V` and a pseudo-matrix `B`, return the lattice spanned by the pseudo-matrix `B` inside `V`. If `V` is hermitian (resp. quadratic) then the output is a hermitian (resp. quadratic) lattice.

By default, `B` is checked to be of full rank. This test can be disabled by setting `check` to false.
