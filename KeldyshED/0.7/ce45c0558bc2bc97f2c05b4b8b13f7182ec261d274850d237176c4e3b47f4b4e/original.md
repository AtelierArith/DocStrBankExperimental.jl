```julia
operator_blocks(
    ed::KeldyshED.EDCore{EDScalarType<:Number},
    op::KeldyshED.Operators.OperatorExpr{OPScalarType<:Number}
) -> Dict{Tuple{Int64, Int64}, Matrix{_A}} where _A

```

Compute blocks of the matrix representation of an operator.

The computed blocks are returned as a dictionary `(initial subspace index, final subspace index) => matrix`, and the matrices are written in the eigenbasis of the Hamiltonian.

## Arguments

  * `ed`:       The Exact Diagonalization solver object.
  * `op`:       Operator expression.
