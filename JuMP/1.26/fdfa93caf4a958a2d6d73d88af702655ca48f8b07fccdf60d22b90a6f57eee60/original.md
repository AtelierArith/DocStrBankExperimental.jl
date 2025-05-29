```
SecondOrderCone
```

Second order cone object that can be used to constrain the euclidean norm of a vector `x` to be less than or equal to a nonnegative scalar `t`.

This is a shortcut for the [`MOI.SecondOrderCone`](@ref) set.

## Example

The following constrains $\|(x-1, x-2)\|_2 \le t$ and $t \ge 0$:

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @variable(model, t)
t

julia> @constraint(model, [t, x-1, x-2] in SecondOrderCone())
[t, x - 1, x - 2] ∈ MathOptInterface.SecondOrderCone(3)
```
