```
construct_hamiltonian([T, ]sys, terms...[; field, auto_pbc_field])
construct_hamiltonian([T, ]lat[, internal, terms...; field, auto_pbc_field])
```

Construct a Hamiltonian for the given system. Does the same as `construct_operator`, but wraps the result in a `Hamiltonian` type.
