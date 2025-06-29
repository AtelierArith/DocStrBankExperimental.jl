```julia
monomial_connection(
    ed::KeldyshED.EDCore,
    mon::KeldyshED.Operators.Monomial,
    sp_index::Int64
) -> Union{Nothing, Int64}

```

Extract a subspace-to-subspace connection generated by a monomial operator (a product of canonical operators $c$/$c^\dagger$) from an Exact Diagonalization solver. Returns `nothing` if no such connection exists.

## Arguments

  * `ed`:       The Exact Diagonalization solver object.
  * `mon`:      Monomial in question.
  * `sp_index`: Initial subspace index.
