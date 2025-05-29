```
Scenarios(
    base_scenario::AbstractDict, 
    uncertainties::AbstractVector{Uncertainty},
    metrics::AbstractVector{String};
    Nscenarios::Int=100,
    Nparallel::Int=1,
    ngens::Int=100
)
```

### Args

  * `base_scenario::AbstractDict` 基本的な REopt シナリオを定義する `Dict`` (詳細は [REopt docs](https://nrel.github.io/REopt.jl/stable/reopt/inputs/#Scenario) を参照)
  * `uncertainties::AbstractVector{Uncertainty}` [Uncertainty](@ref) のベクトル
  * `metrics::AbstractVector{String}` 出力メトリクスのベクトル (TODO これらを分析ツールに使用)

### Keyword Args

  * `Nscenarios::Int` ラテンハイパーキューブからサンプリングするシナリオの数
  * `Nparallel::Int` 並行して実行するシナリオの数 ([Run Threaded Scenarios](@ref) を使用する場合)
  * `ngens::Int` LatinHypercubeSampling.LHCoptim のハイパーパラメータで、サンプルのラテンハイパーキューブを作成するために使用される
