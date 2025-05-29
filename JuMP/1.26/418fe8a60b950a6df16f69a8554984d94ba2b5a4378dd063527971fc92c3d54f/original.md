```
model_convert(
    model::AbstractModel,
    rhs::Union{
        AbstractConstraint,
        Number,
        AbstractJuMPScalar,
        MOI.AbstractSet,
    },
)
```

Convert the coefficients and constants of functions and sets in the `rhs` to the coefficient type `value_type(typeof(model))`.

## Purpose

Creating and adding a constraint is a two-step process. The first step calls [`build_constraint`](@ref), and the result of that is passed to [`add_constraint`](@ref).

However, because [`build_constraint`](@ref) does not take the `model` as an argument, the coefficients and constants of the function or set might be different than `value_type(typeof(model))`.

Therefore, the result of [`build_constraint`](@ref) is converted in a call to `model_convert` before the result is passed to [`add_constraint`](@ref).
