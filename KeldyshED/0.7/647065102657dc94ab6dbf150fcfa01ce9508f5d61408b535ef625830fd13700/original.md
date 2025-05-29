```julia
monomial_matrix(
    ed::KeldyshED.EDCore{ScalarType<:Number},
    mon::KeldyshED.Operators.Monomial,
    sp_index::Int64
) -> Any

```

Extract a non-vanishing matrix block a monomial operator (a product of canonical operators $c$/$c^\dagger$) from an Exact Diagonalization solver. The block is written in the eigenbasis of the Hamiltonian.

## Arguments

  * `ed`:       The Exact Diagonalization solver object.
  * `mon`:      Monomial in question.
  * `sp_index`: Initial subspace index.

The final subspace index is uniquely determined by the pair (`mon`, `sp_index`) as there is at most one non-vanishing matrix per such a pair.
