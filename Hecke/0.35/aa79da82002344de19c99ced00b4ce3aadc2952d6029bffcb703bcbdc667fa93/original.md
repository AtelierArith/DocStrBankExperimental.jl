```
lattice(V::AbstractSpace, basis::MatElem ; check::Bool = true) -> AbstractLat
```

Given an ambient space `V` and a matrix `basis`, return the lattice spanned by the rows of `basis` inside `V`. If `V` is hermitian (resp. quadratic) then the output is a hermitian (resp. quadratic) lattice.

By default, `basis` is checked to be of full rank. This test can be disabled by setting `check` to false.
