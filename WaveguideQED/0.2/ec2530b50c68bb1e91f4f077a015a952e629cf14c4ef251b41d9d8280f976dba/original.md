```
NLevelWaveguideOperator{B1,B2} <: NWaveguideOperator{BL,BR}
```

Structure for fast simultaneous N-level transition and waveguide operator. This operator combines a transition operator between levels in an N-level system with a waveguide operator.

# Fields

  * `basis_l::B1`: Left basis
  * `basis_r::B2`: Right basis
  * `factor::ComplexF64`: Complex prefactor
  * `op::AbstractOperator`: The waveguide operator
  * `loc`: Location indices for the operator
  * `n_to::Int`: Target level for the transition
  * `n_from::Int`: Source level for the transition
  * `indexing::WaveguideIndexing`: Indexing structure for efficient state vector multiplication

# Examples

```julia
# Create a transition between levels 2 and 1 in an N-level system combined with a waveguide operator
op = NLevelWaveguideOperator(basis_l, basis_r, 1.0, waveguide_op, [1,2], 2, 1)
```
