```julia
ptranspose(ρ, idims, isystems)

```

  * `ρ`: quantum state.
  * `idims`: dimensins of subsystems.
  * `isystems`: transposed subsystems.

Return [partial transposition](http://en.wikipedia.org/wiki/Peres-Horodecki_criterion) of matrix `ρ` over the subsystems determined by `isystems`.
