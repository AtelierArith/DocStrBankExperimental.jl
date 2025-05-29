```
tightbinding_hamiltonian([T, ]sys[, args...; t1=1, t2=0, t3=0, field, auto_pbc_field])
tightbinding_hamiltonian([T, ]lat[, internal, args...; t1=1, t2=0, t3=0, field, auto_pbc_field])
```

Construct a tight-binding Hamiltonian for the given system.

## Arguments

  * `T`: The element type of the Hamiltonian. Default is `ComplexF64`.
  * `sys`: The `System` for which the Hamiltonian is constructed.
  * `lat`: The lattice for which the Hamiltonian is constructed.
  * `internal`: The basis for the internal degrees of freedom.

All other arguments are interpreted as terms of the Hamiltonian and passed to `construct_hamiltonian`.

## Keyword Arguments

  * `t1`, `t2`, `t3`: The hopping amplitudes for the nearest, next-nearest, and next-next-nearest   neighbors, respectively.
  * `field`: The gauge field to use for the bond operators. Default is `NoField()`.
  * `auto_pbc_field`: Whether to automatically adapt the field to the periodic boundary   conditions of the lattice. Defaults to `true`.
