```
is_maximal_integral(L::AbstractLat) -> Bool, AbstractLat
```

Given a lattice `L`, return whether `L` has integral norm and has no proper overlattice satisfying this property.

If the norm of `L` is not integral, the second output is `L` by default. Otherwise, either `L` is maximal and the second output is `L`, or the second output is a minimal overlattice `M` of `L` with integral norm.
