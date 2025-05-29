```julia
cdag_matrix(
    ed::KeldyshED.EDCore,
    op_linear_index::Int64,
    sp_index::Int64
) -> Matrix{ScalarType} where ScalarType<:Number

```

Extract a non-vanishing matrix block of a creation operator from an Exact Diagonalization solver. The block is written in the eigenbasis of the Hamiltonian.

## Arguments

  * `ed`:              The Exact Diagonalization solver object.
  * `op_linear_index`: Linear index of the creation operator as defined by                    `ed.full_hs.soi`.
  * `sp_index`:        Initial subspace index.

The final subspace index is uniquely determined by the pair (`op_linear_index`, `sp_index`) as there is at most one non-vanishing matrix per such a pair.
