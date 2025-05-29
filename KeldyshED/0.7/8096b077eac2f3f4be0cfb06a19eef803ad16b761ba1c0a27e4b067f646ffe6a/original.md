```julia
operator_blocks(
    ed::KeldyshED.EDCore{EDScalarType<:Number},
    op::KeldyshED.Operators.OperatorExpr{OPScalarType<:Number},
    sp_index::Int64
) -> Dict{Int64, Matrix{_A}} where _A

```

Compute blocks of the matrix representation of an operator acting on states in a given (initial) subspace. The computed blocks are returned as a dictionary `final subspace index => matrix`, and the matrices are written in the eigenbasis of the Hamiltonian.

## Arguments

  * `ed`:       The Exact Diagonalization solver object.
  * `op`:       Operator expression.
  * `sp_index`: Initial subspace index.
