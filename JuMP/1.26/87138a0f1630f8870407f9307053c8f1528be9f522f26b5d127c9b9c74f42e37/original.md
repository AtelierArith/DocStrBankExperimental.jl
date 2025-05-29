```
HermitianPSDCone
```

Hermitian positive semidefinite cone object that can be used to create a Hermitian positive semidefinite square matrix in the [`@variable`](@ref) and [`@constraint`](@ref) macros.

## Example

Consider the following example:

```jldoctest
julia> model = Model();

julia> @variable(model, H[1:3, 1:3] in HermitianPSDCone())
3×3 LinearAlgebra.Hermitian{GenericAffExpr{ComplexF64, VariableRef}, Matrix{GenericAffExpr{ComplexF64, VariableRef}}}:
 real(H[1,1])                    …  real(H[1,3]) + imag(H[1,3]) im
 real(H[1,2]) - imag(H[1,2]) im     real(H[2,3]) + imag(H[2,3]) im
 real(H[1,3]) - imag(H[1,3]) im     real(H[3,3])

julia> c = constraint_object(VariableInSetRef(H));

julia> c.func
9-element Vector{VariableRef}:
 real(H[1,1])
 real(H[1,2])
 real(H[2,2])
 real(H[1,3])
 real(H[2,3])
 real(H[3,3])
 imag(H[1,2])
 imag(H[1,3])
 imag(H[2,3])

julia> c.set
MathOptInterface.HermitianPositiveSemidefiniteConeTriangle(3)
```

We see in the output of the last commands that 9 real variables were created. The matrix `H` constrains affine expressions in terms of these 9 variables that parametrize a Hermitian matrix.
