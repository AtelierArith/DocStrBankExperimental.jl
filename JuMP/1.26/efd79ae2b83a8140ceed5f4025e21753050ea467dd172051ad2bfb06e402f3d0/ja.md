```
set_objective(model::AbstractModel, sense::MOI.OptimizationSense, func)
```

[`@objective`](@ref) マクロの機能的な同等物です。

この関数は、目的の感覚と目的関数を同時に設定し、[`set_objective_sense`](@ref) の後に [`set_objective_function`](@ref) を呼び出すことと同等です。

これは低レベルの関数です。目的関数と感覚を設定する推奨方法は、[`@objective`](@ref) マクロを使用することです。

## FEASIBILITY_SENSE

`sense` を [`FEASIBILITY_SENSE`](@ref) に設定してはいけません。なぜなら、[`FEASIBILITY_SENSE`](@ref) は目的関数が存在しないことを意味するからです。

`set_objective(model, FEASIBILITY_SENSE, f)` の代わりに、`set_objective_sense(model, FEASIBILITY_SENSE)` を行ってください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> set_objective(model, MIN_SENSE, x)

julia> objective_sense(model)
MIN_SENSE::OptimizationSense = 0

julia> objective_function(model)
x
```
