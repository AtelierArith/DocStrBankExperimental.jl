```
MultTable(ops::AbstractVector, modτ=true)
```

Compute the multiplication (or Cayley) table of `ops`, an iterable of `SymOperation`s.

A `MultTable` is returned, which contains symmetry operations resulting from composition  of `row` and `col` operators; the table of indices give the symmetry operators relative to the ordering of `ops`.

## Keyword arguments

  * `modτ` (default: `true`): whether composition of operations is taken modulo lattice

vectors (`true`) or not (`false`).
