```
tmeet(𝕃::AbstractLattice, a, b::Type)
```

Compute the lattice meet of lattice elements `a` and `b` over the lattice `𝕃`, dropping any results that will not be inhabited at runtime. If `𝕃` is `JLTypeLattice`, this is equivalent to type intersection plus the elimination of results that have no concrete subtypes. Note that currently `b` is restricted to being a type (interpreted as a lattice element in the `JLTypeLattice` sub-lattice of `𝕃`).
