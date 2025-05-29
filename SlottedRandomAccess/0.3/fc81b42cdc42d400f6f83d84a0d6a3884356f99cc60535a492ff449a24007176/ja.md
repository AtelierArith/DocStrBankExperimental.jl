```julia
struct PLR_Simulation
```

PLRシミュレーションのパラメータと結果を含む型。

# フィールド

  * `params::SlottedRandomAccess.PLR_SimulationParameters`: シミュレーションに使用されるパラメータ
  * `results::StructArrays.StructArray{SlottedRandomAccess.PLR_Simulation_Point}`: シミュレーションの結果
  * `scatter_kwargs::Dict{Symbol, Any}`: プロットのためのscatter呼び出しに渡されるキーワード引数のリスト

# コンストラクタ

```
PLR_Simulation(load::AbstractVector; kwargs...)
```

負荷ベクトルを提供することで`PLR_Simulation`オブジェクトを作成します。これにより、すべての`kwargs`が[`PLR_SimulationParameters`](@ref)コンストラクタに転送されます。

```
PLR_Simulation(load::AbstractVector, params::PLR_SimulationParameters; scatter_kwargs = Dict{Symbol, Any}())
```

このコンストラクタは、負荷と`params`フィールドの両方を位置引数として直接提供することを許可します。PlotlyBaseからの`scatter`呼び出しに渡すカスタムキーワード引数は、デフォルトで空の`Dict`となる`scatter_kwargs`キーワード引数を使用して提供できます。

参照: [`PLR_SimulationParameters`](@ref)
