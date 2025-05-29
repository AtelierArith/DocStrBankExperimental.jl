```
set_normalized_coefficient(
    constraints::AbstractVector{
        <:ConstraintRef{<:AbstractModel,<:MOI.ConstraintIndex{F}},
    },
    variables::AbstractVector{<:AbstractVariableRef},
    coeffs::AbstractVector{<:Number},
) where {
    T,
    F<:Union{MOI.ScalarAffineFunction{T},MOI.ScalarQuadraticFunction{T}},
}
```

Set multiple coefficient of `variables` in the constraints `constraints` to `coeffs`.

## Concrete types

Note that `constraints` must be a concrete vector of a single constraint type. You cannot mix, for example, `<=` and `>=` constraints in the same vector.

## Normalization

Note that prior to this step, JuMP will aggregate multiple terms containing the same variable. For example, given a constraint `2x + 3x <= 2`, `set_normalized_coefficient(con, [x], [4])` will create the constraint `4x <= 2`.

## Example

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x)
x

julia> @variable(model, y)
y

julia> @constraint(model, con, 2x + 3x + 4y <= 2)
con : 5 x + 4 y ≤ 2

julia> set_normalized_coefficient([con, con], [x, y], [6, 7])

julia> con
con : 6 x + 7 y ≤ 2
```
