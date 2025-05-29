```
PSDCone
```

Positive semidefinite cone object that can be used to constrain a square matrix to be positive semidefinite in the [`@constraint`](@ref) macro. If the matrix has type `Symmetric` then the columns vectorization (the vector obtained by concatenating the columns) of its upper triangular part is constrained to belong to the `MOI.PositiveSemidefiniteConeTriangle` set, otherwise its column vectorization is constrained to belong to the `MOI.PositiveSemidefiniteConeSquare` set.

## Examples

Consider the following example:

```jldoctest PSDCone; setup = :(using JuMP)
julia> model = Model();

julia> @variable(model, x)
x

julia> a = [ x 2x
            2x  x];

julia> b = [1 2
            2 4];

julia> cref = @constraint(model, a >= b, PSDCone())
[x - 1    2 x - 2;
 2 x - 2  x - 4  ] ∈ PSDCone()

julia> jump_function(constraint_object(cref))
4-element Array{GenericAffExpr{Float64,VariableRef},1}:
 x - 1
 2 x - 2
 2 x - 2
 x - 4

julia> moi_set(constraint_object(cref))
MathOptInterface.PositiveSemidefiniteConeSquare(2)
```

We see in the output of the last command that the matrix the vectorization of the matrix is constrained to belong to the `PositiveSemidefiniteConeSquare`.

```jldoctest PSDCone
julia> using LinearAlgebra # For Symmetric

julia> cref = @constraint(model, Symmetric(a - b) in PSDCone())
[x - 1    2 x - 2;
 2 x - 2  x - 4  ] ∈ PSDCone()

julia> jump_function(constraint_object(cref))
3-element Array{GenericAffExpr{Float64,VariableRef},1}:
 x - 1
 2 x - 2
 x - 4

julia> moi_set(constraint_object(cref))
MathOptInterface.PositiveSemidefiniteConeTriangle(2)
```

As we see in the output of the last command, the vectorization of only the upper triangular part of the matrix is constrained to belong to the `PositiveSemidefiniteConeSquare`.
