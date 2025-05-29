```
RotatedSecondOrderCone
```

Rotated second order cone object that can be used to constrain the square of the euclidean norm of a vector `x` to be less than or equal to $2tu$ where `t` and `u` are nonnegative scalars.

This is a shortcut for the [`MOI.RotatedSecondOrderCone`](@ref) set.

## Example

The following constrains $\|(x-1, x-2)\|^2_2 \le 2tx$ and $t, x \ge 0$:

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @variable(model, t)
t

julia> @constraint(model, [t, x, x-1, x-2] in RotatedSecondOrderCone())
[t, x, x - 1, x - 2] ∈ MathOptInterface.RotatedSecondOrderCone(4)
```
