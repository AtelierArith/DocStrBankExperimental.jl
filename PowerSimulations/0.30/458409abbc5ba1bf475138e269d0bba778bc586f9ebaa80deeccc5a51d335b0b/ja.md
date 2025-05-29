```julia
execute!(
    sim::PowerSimulations.Simulation;
    kwargs...
) -> InfrastructureSystems.Simulation.RunStatusModule.RunStatus

```

シミュレーションのモデルを逐次シミュレーションのために解決します。

# 引数

  * `sim::Simulation=sim`: Simulation()によって作成されたシミュレーションオブジェクト

オプションのキーワード引数`exports`は、シミュレーションが実行される際の結果をCSVファイルにエクスポートすることを制御します。

# 例

```julia
sim = Simulation("Test", 7, problems, "/Users/folder")
execute!(sim::Simulation; kwargs...)
```
