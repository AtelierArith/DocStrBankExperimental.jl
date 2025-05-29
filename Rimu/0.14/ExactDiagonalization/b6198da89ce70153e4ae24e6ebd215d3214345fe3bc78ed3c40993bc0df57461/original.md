```
sparse(hamiltonian::AbstractHamiltonian, addr=starting_address(hamiltonian); kwargs...)
sparse(bsr::BasisSetRepresentation)
```

Return a sparse matrix representation of `hamiltonian` or `bsr`. `kwargs` are passed to [`BasisSetRepresentation`](@ref).

See [`BasisSetRepresentation`](@ref).
