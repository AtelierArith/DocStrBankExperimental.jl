```
is_density_matrix( ρ :: Matrix; atol=ATOL :: Float64 ) :: Bool
```

Returns `true` if `ρ` is a valid density matrix. The following constraints must be satisfied for all density matrices:

  * Hermitian: `ρ' == ρ`
  * Positive Semidefinite: `eigmin(ρ) ≥ 0`
  * Trace-one: `tr(ρ) == 1`
