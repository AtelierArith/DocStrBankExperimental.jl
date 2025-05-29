```
set_nonlinear_dual_start_value(
    model::Model,
    start::Union{Nothing,Vector{Float64}},
)
```

Set the value of the MOI attribute [`MOI.NLPBlockDualStart`](@ref).

The start vector corresponds to the Lagrangian duals of the nonlinear constraints, in the order given by [`all_nonlinear_constraints`](@ref). That is, you must pass a single start vector corresponding to all of the nonlinear constraints in a single function call; you cannot set the dual start value of nonlinear constraints one-by-one. The example below demonstrates how to use [`all_nonlinear_constraints`](@ref) to create a mapping between the nonlinear constraint references and the start vector.

Pass `nothing` to unset a previous start.

## Examples

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> nl1 = @NLconstraint(model, x[1] <= sqrt(x[2]));

julia> nl2 = @NLconstraint(model, x[1] >= exp(x[2]));

julia> start = Dict(nl1 => -1.0, nl2 => 1.0);

julia> start_vector = [start[con] for con in all_nonlinear_constraints(model)]
2-element Vector{Float64}:
 -1.0
  1.0

julia> set_nonlinear_dual_start_value(model, start_vector)

julia> nonlinear_dual_start_value(model)
2-element Vector{Float64}:
 -1.0
  1.0
```
