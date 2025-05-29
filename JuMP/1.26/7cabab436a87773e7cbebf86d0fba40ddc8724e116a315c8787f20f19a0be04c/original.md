```
direct_generic_model(::Type{T}, factory::MOI.OptimizerWithAttributes)
```

Create a [`direct_generic_model`](@ref) using `factory`, a `MOI.OptimizerWithAttributes` object created by [`optimizer_with_attributes`](@ref).

## Example

```jldoctest
julia> import HiGHS

julia> optimizer = optimizer_with_attributes(
           HiGHS.Optimizer,
           "presolve" => "off",
           MOI.Silent() => true,
       );

julia> model = direct_generic_model(Float64, optimizer)
A JuMP Model
├ mode: DIRECT
├ solver: HiGHS
├ objective_sense: FEASIBILITY_SENSE
├ num_variables: 0
├ num_constraints: 0
└ Names registered in the model: none
```

is equivalent to:

```jldoctest
julia> import HiGHS

julia> model = direct_generic_model(Float64, HiGHS.Optimizer())
A JuMP Model
├ mode: DIRECT
├ solver: HiGHS
├ objective_sense: FEASIBILITY_SENSE
├ num_variables: 0
├ num_constraints: 0
└ Names registered in the model: none

julia> set_attribute(model, "presolve", "off")

julia> set_attribute(model, MOI.Silent(), true)
```
