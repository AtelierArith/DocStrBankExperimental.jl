```
lattice(V::AbstractSpace, gens::Vector) -> AbstractLat
```

Given an ambient space `V` and a list of generators `gens`, return the lattice spanned by `gens` in `V`. If `V` is hermitian (resp. quadratic) then the output is a hermitian (resp. quadratic) lattice.

If `gens` is empty, the function returns the zero lattice in `V`.
