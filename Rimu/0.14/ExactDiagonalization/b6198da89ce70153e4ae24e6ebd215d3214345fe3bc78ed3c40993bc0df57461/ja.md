```
sparse(hamiltonian::AbstractHamiltonian, addr=starting_address(hamiltonian); kwargs...)
sparse(bsr::BasisSetRepresentation)
```

`hamiltonian` または `bsr` のスパース行列表現を返します。`kwargs` は [`BasisSetRepresentation`](@ref) に渡されます。

[`BasisSetRepresentation`](@ref) を参照してください。
