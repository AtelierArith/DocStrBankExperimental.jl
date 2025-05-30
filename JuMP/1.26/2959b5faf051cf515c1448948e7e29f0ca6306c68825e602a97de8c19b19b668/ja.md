```
@objective(model::GenericModel, sense, func)
```

目的の感覚を`sense`に、目的関数を`func`に設定します。

## `sense`

目的の感覚は、リテラル`Min`または`Max`のいずれか、または三つの[`MOI.OptimizationSense`](@ref)列挙型の値（[`MIN_SENSE`](@ref)、[`MAX_SENSE`](@ref)、または[`FEASIBILITY_SENSE`](@ref)）のいずれかでなければなりません。

プログラム的に感覚を設定するには、すなわち`sense`が感覚の値を持つJulia変数である場合、[`MOI.OptimizationSense`](@ref)を使用する必要があります。

## FEASIBILITY_SENSE

[`FEASIBILITY_SENSE`](@ref)は、目的関数が存在しないことを意味します。したがって、非ゼロの`func`で`sense`を[`FEASIBILITY_SENSE`](@ref)に設定してはいけません。

モデルを[`FEASIBILITY_SENSE`](@ref)にリセットするには、`@objective(model, FEASIBILITY_SENSE, 0)`を実行するか、[`set_objective_sense`](@ref)を使用します：`set_objective_sense(model, FEASIBILITY_SENSE)`。

## 例

変数`x`の値を最小化するには、次のようにします：

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @objective(model, Min, x)
x
```

アフィン式`2x - 1`の値を最大化します：

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @objective(model, Max, 2x - 1)
2 x - 1
```

プログラム的に目的の感覚を設定します：

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> sense = MIN_SENSE
MIN_SENSE::OptimizationSense = 0

julia> @objective(model, sense, x^2 - 2x + 1)
x² - 2 x + 1
```

目的関数を削除します：

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0);

julia> @objective(model, Min, 2x + 1)
2 x + 1

julia> print(model)
Min 2 x + 1
Subject to
 x ≥ 0

julia> @objective(model, FEASIBILITY_SENSE, 0)
0

julia> print(model)
Feasibility
Subject to
 x ≥ 0
```
