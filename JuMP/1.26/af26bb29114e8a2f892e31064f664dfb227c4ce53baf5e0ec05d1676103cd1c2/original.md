```
PSDCone
```

Positive semidefinite cone object that can be used to constrain a square matrix to be positive semidefinite in the [`@constraint`](@ref) macro.

If the matrix has type `Symmetric` then the columns vectorization (the vector obtained by concatenating the columns) of its upper triangular part is constrained to belong to the [`MOI.PositiveSemidefiniteConeTriangle`](@ref) set, otherwise its column vectorization is constrained to belong to the [`MOI.PositiveSemidefiniteConeSquare`](@ref) set.

## Example

Non-symmetric case:

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> a = [x 2x; 2x x];

julia> b = [1 2; 2 4];

julia> cref = @constraint(model, a >= b, PSDCone())
[x - 1    2 x - 2
 2 x - 2  x - 4] ∈ PSDCone()

julia> jump_function(constraint_object(cref))
4-element Vector{AffExpr}:
 x - 1
 2 x - 2
 2 x - 2
 x - 4

julia> moi_set(constraint_object(cref))
MathOptInterface.PositiveSemidefiniteConeSquare(2)
```

Symmetric case:

```jldoctest PSDCone
julia> using LinearAlgebra # For Symmetric

julia> model = Model();

julia> @variable(model, x);

julia> a = [x 2x; 2x x];

julia> b = [1 2; 2 4];

julia> cref = @constraint(model, Symmetric(a - b) in PSDCone())
[x - 1  2 x - 2
 ⋯      x - 4] ∈ PSDCone()

julia> jump_function(constraint_object(cref))
3-element Vector{AffExpr}:
 x - 1
 2 x - 2
 x - 4

julia> moi_set(constraint_object(cref))
MathOptInterface.PositiveSemidefiniteConeTriangle(2)
```
