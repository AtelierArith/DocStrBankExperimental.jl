```
HermitianMatrixSpace()
```

Use in the [`@variable`](@ref) macro to constrain a matrix of variables to be hermitian.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, Q[1:2, 1:2] in HermitianMatrixSpace())
2×2 LinearAlgebra.Hermitian{GenericAffExpr{ComplexF64, VariableRef}, Matrix{GenericAffExpr{ComplexF64, VariableRef}}}:
 real(Q[1,1])                    real(Q[1,2]) + imag(Q[1,2]) im
 real(Q[1,2]) - imag(Q[1,2]) im  real(Q[2,2])
```
