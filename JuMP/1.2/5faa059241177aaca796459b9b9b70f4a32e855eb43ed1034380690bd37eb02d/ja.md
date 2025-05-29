```
@objective(model::Model, sense, func)
```

目的の感覚を`sense`に、目的関数を`func`に設定します。目的の感覚は`Min`、`Max`、`MathOptInterface.MIN_SENSE`、`MathOptInterface.MAX_SENSE`、または`MathOptInterface.FEASIBILITY_SENSE`のいずれかである必要があります。詳細は[`MathOptInterface.ObjectiveSense`](https://jump.dev/MathOptInterface.jl/stable/reference/models/#MathOptInterface.ObjectiveSense)を参照してください。感覚をプログラム的に設定するためには、すなわち`sense`が感覚の値を持つJulia変数である場合、3つの`MathOptInterface.ObjectiveSense`の値のいずれかを使用する必要があります。関数`func`は、単一のJuMP変数、JuMP変数のアフィン式、またはJuMP変数の二次式であることができます。

## 例

変数`x`の値を最小化するには、次のようにします：

```jldoctest @objective; setup = :(using JuMP)
julia> model = Model()
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.

julia> @variable(model, x)
x

julia> @objective(model, Min, x)
x
```

アフィン式`2x - 1`の値を最大化するには、次のようにします：

```jldoctest @objective
julia> @objective(model, Max, 2x - 1)
2 x - 1
```

二次目的を設定し、目的の感覚をプログラム的に設定するには、次のようにします：

```jldoctest @objective
julia> sense = MIN_SENSE
MIN_SENSE::OptimizationSense = 0

julia> @objective(model, sense, x^2 - 2x + 1)
x² - 2 x + 1
```
