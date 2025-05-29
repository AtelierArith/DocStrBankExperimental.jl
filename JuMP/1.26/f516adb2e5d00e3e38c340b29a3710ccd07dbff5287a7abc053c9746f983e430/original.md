```
set_start_value(con_ref::ConstraintRef, value)
```

Set the primal start value ([`MOI.ConstraintPrimalStart`](@ref)) of the constraint `con_ref` to `value`.

To remove a primal start value set it to `nothing`.

See also [`start_value`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x, start = 2.0);

julia> @constraint(model, c, [2x] in Nonnegatives())
c : [2 x] ∈ Nonnegatives()

julia> set_start_value(c, [4.0])

julia> start_value(c)
1-element Vector{Float64}:
 4.0

julia> set_start_value(c, nothing)

julia> start_value(c)
```
