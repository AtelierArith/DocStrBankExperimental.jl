```
construct_operator([T, ]sys, terms...[; field, auto_pbc_field])
construct_operator([T, ]lat[, internal, terms...; field])
```

Construct an operator for the given system.

Each of the `terms` describes a term of the Hamiltonian. The term can be given in several ways:

  * A `DataOperator` on the lattice, internal or composite basis (will be matched automatically).
  * A `Pair` of an "internal" and an "on-lattice" part (e.g. `int_p => lat_p`):

      * The "internal" part can be a `DataOperator`, a matrix or a number.
      * The "on-lattice" part can be a `LatticeValue` (represents a diagonal term), a site   (represents a local on-site potential), a bond (represents a hopping term) or a `site1 => site2`   pair (represents a single hopping).
      * Identity "internal" or "on-lattice" parts can be omitted.

See documentation for more details.

## Arguments

  * `T`: The element type of the Hamiltonian. Default is `ComplexF64`.
  * `sys`: The `System` for which the Hamiltonian is constructed.
  * `lat`: The lattice for which the Hamiltonian is constructed.
  * `internal`: The basis for the internal degrees of freedom.

## Keyword Arguments

  * `field`: The gauge field to use for the bond operators. Default is `NoField()`.
  * `auto_pbc_field`: Whether to automatically adapt the field to the periodic boundary   conditions of the lattice. Defaults to `true`.
