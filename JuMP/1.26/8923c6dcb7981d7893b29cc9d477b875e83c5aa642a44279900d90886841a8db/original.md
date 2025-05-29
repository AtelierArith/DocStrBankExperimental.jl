```
dual_start_value(con_ref::ConstraintRef)
```

Return the dual start value (MOI attribute `ConstraintDualStart`) of the constraint `con_ref`.

If no dual start value has been set, `dual_start_value` will return `nothing`.

See also [`set_dual_start_value`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x, start = 2.0);

julia> @constraint(model, c, [2x] in Nonnegatives())
c : [2 x] ∈ Nonnegatives()

julia> set_dual_start_value(c, [0.0])

julia> dual_start_value(c)
1-element Vector{Float64}:
 0.0

julia> set_dual_start_value(c, nothing)

julia> dual_start_value(c)
```
