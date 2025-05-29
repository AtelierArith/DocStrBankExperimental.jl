```
set_objective_function(model::GenericModel, func::MOI.AbstractFunction)
set_objective_function(model::GenericModel, func::AbstractJuMPScalar)
set_objective_function(model::GenericModel, func::Real)
set_objective_function(model::GenericModel, func::Vector{<:AbstractJuMPScalar})
```

`model`の目的関数を与えられた関数`func`に設定します。

参照: [`@objective`](@ref), [`set_objective_function`](@ref), [`set_objective`](@ref)

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @objective(model, Min, x);

julia> objective_function(model)
x

julia> set_objective_function(model, 2 * x + 1)

julia> objective_function(model)
2 x + 1
```
