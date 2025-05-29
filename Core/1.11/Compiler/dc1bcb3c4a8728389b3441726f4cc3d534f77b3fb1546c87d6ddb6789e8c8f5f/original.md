```
is_lattice_equal(𝕃::AbstractLattice, a, b) -> Bool
```

Check if two lattice elements are partial order equivalent. This is basically `a ⊑ b && b ⊑ a` in the lattice of `𝕃` but (optionally) with extra performance optimizations.
