```
SymmetricMatrixSpace()
```

Use in the [`@variable`](@ref) macro to constrain a matrix of variables to be symmetric.

## Examples

```jldoctest; setup=:(model = Model())
julia> @variable(model, Q[1:2, 1:2] in SymmetricMatrixSpace())
2×2 LinearAlgebra.Symmetric{VariableRef,Array{VariableRef,2}}:
 Q[1,1]  Q[1,2]
 Q[1,2]  Q[2,2]
```
