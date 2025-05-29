```julia
cdag_matrix(
    ed::KeldyshED.EDCore,
    indices::Vector{Union{Int64, String}},
    sp_index::Int64
) -> Matrix{ScalarType} where ScalarType<:Number

```

Extract a non-vanishing matrix block of a creation operator from an Exact Diagonalization solver. The block is written in the eigenbasis of the Hamiltonian.

## Arguments

  * `ed`:       The Exact Diagonalization solver object.
  * `indices`:  Compound index of the creation operator (must be part of             `ed.full_hs.soi`).
  * `sp_index`: Initial subspace index.

The final subspace index is uniquely determined by the pair (`indices`, `sp_index`) as there is at most one non-vanishing matrix per such a pair.
