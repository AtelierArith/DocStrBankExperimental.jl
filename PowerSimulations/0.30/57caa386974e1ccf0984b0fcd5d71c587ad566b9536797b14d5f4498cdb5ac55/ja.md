```julia
build!(
    sim::PowerSimulations.Simulation;
    recorders,
    console_level,
    file_level,
    serialize,
    partitions,
    index
) -> InfrastructureSystems.Simulation.SimulationBuildStatusModule.SimulationBuildStatus

```

シミュレーションを構築し、問題と関連するフォルダ構造を作成します。

# 引数

  * `sim::Simulation`: シミュレーションオブジェクト
  * `recorders::Vector{Symbol} = []`: 登録するレコーダー名
  * `serialize::Bool = true`: シミュレーション内のシミュレーションオブジェクトをシリアライズする
  * `console_level = Logging.Error`:
  * `file_level = Logging.Info`:
