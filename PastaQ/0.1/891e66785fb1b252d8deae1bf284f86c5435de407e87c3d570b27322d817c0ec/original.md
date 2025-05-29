```
randombases(n::Int, nbases::Int; local_basis = "Pauli")
```

Generate `nbases` measurement bases composed by $n$ single-qubit bases. By default, each local basis is randomly selected between Pauli bases `["X","Y","Z"]`, with `"Z"` being the default basis where the quantum state is written.

The measurement bases can also be defined by the user, `local_basis = [O1, O2,...]`, as long as the single-qubit Hermitian operators $O_j$ are defined.
