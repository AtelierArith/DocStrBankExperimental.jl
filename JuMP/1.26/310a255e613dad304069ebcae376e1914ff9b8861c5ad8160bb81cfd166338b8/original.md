```
VariableInSetRef(
    model::GenericModel,
    x::Union{AbstractJuMPScalar,AbstractArray{<:AbstractJuMPScalar}},
)
```

Return the constraint reference associated with `x` when it is constrained on creation.

A variable is constrained on creation if it uses the `x in S` or `x, set = S` syntax in the [`@variable`](@ref) macro.

This function errors if `x` was not constrained on creation. To check if the variable was constrained on creation, use [`is_variable_in_set`](@ref).

## Exceptions

This function does not apply for variable bounds or integrality restrictions of a scalar variable. For example:

```jldoctest variable_in_set_ref_docstring
julia> model = Model();

julia> @variable(model, x >= 0, Int)
x

julia> is_variable_in_set(x)
false
```

Use instead [`IntegerRef`](@ref), [`BinaryRef`](@ref), [`LowerBoundRef`](@ref), [`UpperBoundRef`](@ref), and [`FixRef`](@ref).

```jldoctest variable_in_set_ref_docstring
julia> model = Model();

julia> @variable(model, x >= 0, Int)
x

julia> IntegerRef(x)
x integer

julia> LowerBoundRef(x)
x ≥ 0
```

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2, 1:2], PSD)
2×2 LinearAlgebra.Symmetric{VariableRef, Matrix{VariableRef}}:
 x[1,1]  x[1,2]
 x[1,2]  x[2,2]

julia> is_variable_in_set(x)
true

julia> c = VariableInSetRef(x)
[x[1,1]  x[1,2]
 ⋯       x[2,2]] ∈ PSDCone()

julia> @variable(model, y)
y

julia> is_variable_in_set(y)
false

julia> @variable(model, z in Semicontinuous(1, 2))
z

julia> is_variable_in_set(z)
true

julia> c_z = VariableInSetRef(z)
z ∈ MathOptInterface.Semicontinuous{Int64}(1, 2)
```
