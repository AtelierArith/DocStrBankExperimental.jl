```
read_hamiltonian(chk::NamedTuple, eigvals::Matrix)
```

Uses the Wannier90 chkpoint info in `chk` and DFT `eigenvals` read with [`read_eig`] to construct the [`TBHamiltonian`](@ref TBOperator).
