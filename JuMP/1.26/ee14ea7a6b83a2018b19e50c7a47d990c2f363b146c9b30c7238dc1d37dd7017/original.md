```
set_dual_start_value(con_ref::ConstraintRef, value)
```

Set the dual start value (MOI attribute `ConstraintDualStart`) of the constraint `con_ref` to `value`.

To remove a dual start value set it to `nothing`.

See also [`dual_start_value`](@ref).

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
