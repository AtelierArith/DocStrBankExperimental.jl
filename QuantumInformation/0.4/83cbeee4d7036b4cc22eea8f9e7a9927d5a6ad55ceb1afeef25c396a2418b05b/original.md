```julia
ptrace(ρ, idims, isystems)

```

  * `ρ`: quantum state.
  * `idims`: dimensins of subsystems.
  * `isystems`: traced subsystems.

Return [partial trace](https://en.wikipedia.org/wiki/Partial_trace) of matrix `ρ` over the subsystems determined by `isystems`.
