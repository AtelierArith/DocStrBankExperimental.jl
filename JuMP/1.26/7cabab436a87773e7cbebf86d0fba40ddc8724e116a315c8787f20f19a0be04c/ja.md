```
direct_generic_model(::Type{T}, factory::MOI.OptimizerWithAttributes)
```

[`direct_generic_model`](@ref)を`factory`、すなわち[`optimizer_with_attributes`](@ref)によって作成された`MOI.OptimizerWithAttributes`オブジェクトを使用して作成します。

## 例

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

は次のように等価です：

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
