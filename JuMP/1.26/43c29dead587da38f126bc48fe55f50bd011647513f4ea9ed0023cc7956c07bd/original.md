```
is_variable_in_set(
    model::GenericModel,
    x::Union{AbstractJuMPScalar,AbstractArray{<:AbstractJuMPScalar}},
)::Bool
```

Return a `Bool` if [`VariableInSetRef`](@ref) returns a valid constraint reference without erroring.

## Exceptions

This function does not apply for variable bounds or integrality restrictions of a scalar variable. For example:

```jldoctest variable_in_set_ref_docstring
julia> model = Model();

julia> @variable(model, x >= 0, Int)
x

julia> is_variable_in_set(x)
false
```

Use instead [`is_integer`](@ref), [`is_binary`](@ref), [`has_lower_bound`](@ref), [`has_upper_bound`](@ref), and [`is_fixed`](@ref).

```jldoctest variable_in_set_ref_docstring
julia> model = Model();

julia> @variable(model, x >= 0, Int)
x

julia> is_integer(x)
true

julia> has_lower_bound(x)
true
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
