```
create_identity_qfunction(c::Ceed, size, inmode::EvalMode, outmode::EvalMode)
```

Create an identity [`QFunction`](@ref). Inputs are written into outputs in the order given. This is useful for [`Operators`](@ref Operator) that can be represented with only the action of a [`ElemRestriction`](@ref) and [`Basis`](@ref), such as restriction and prolongation operators for p-multigrid. Backends may optimize `CeedOperators` with this Q-function to avoid the copy of input data to output fields by using the same memory location for both.
