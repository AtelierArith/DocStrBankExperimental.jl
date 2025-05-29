```
function Simulation
    ::SimulationModel
    system::PowerSystems.System
    simulation_folder::String
    tspan::NTuple{2, Float64},
    perturbations::Vector{<:Perturbation} = Vector{Perturbation}();
    kwargs...,
end
```

シミュレーションオブジェクトを構築し、インデックス処理を実施します。元のシステムは変更されず、そのコピーが作成され、シミュレーションに保存されます。

# 引数:

  * `::SimulationModel` : シミュレーションモデルのタイプ。`ResidualModel`または`MassMatrixModel`。詳細については[Models Section](https://nrel-sienna.github.io/PowerSimulationsDynamics.jl/stable/models/)を参照してください。
  * `system::PowerSystems.System` : システムデータ
  * `simulation_folder::String` : フォルダディレクトリ
  * `tspan::NTuple{2, Float64}` : シミュレーションの時間範囲
  * `perturbations::Vector{<:Perturbation}` : シミュレーションのための摂動のベクトル。デフォルト: 摂動なし
  * `initialize_simulation::Bool` : 初期化ルーチンを実行します。falseの場合、シミュレーションはシステムに保存された運用ポイントに基づいて実行されます。
  * `initial_conditions::Vector{Float64}` : ユーザーがシミュレーションで望む初期条件値を持つベクトルを渡すことを可能にします。initialize_simulation = trueの場合、これらの値は最初の推測として使用され、上書きされます。
  * `frequency_reference` : デフォルトは`ReferenceBus`。ネットワークに使用される周波数モデルを決定します。現在、利用可能なオプションは2つあります：

      * `ConstantFrequency`は、ネットワーク周波数が常に1.0パー単位であると仮定します。
      * `ReferenceBus`は、Reference Bus（電力フローデータで定義された）に接続された動的発電機（ローター速度）または動的インバータ（仮想速度）の周波数状態をネットワーク周波数として使用します。そのようなバスに複数のデバイスが接続されている場合、より大きな基準電力を持つデバイスが参照として使用されます。電圧源がReference Busに接続されている場合、`ConstantFrequency`モデルが使用されます。
  * `system_to_file::Bool` : デフォルトは`false`。初期化されたシステムをシリアライズします。
  * `console_level::Logging` : デフォルトは`Logging.Warn`。コンソールへのログ出力のレベルを設定します。`Logging.Error`、`Logging.Warn`、`Logging.Info`、または`Logging.Debug`に設定できます。
  * `file_level::Logging` : デフォルトは`Logging.Info`。ファイルへのログ出力のレベルを設定します。`Logging.Error`、`Logging.Warn`、`Logging.Info`、または`Logging.Debug`に設定できます。
  * `disable_timer_outputs::Bool` : デフォルトは`false`。シミュレーションの構築と初期化に関するタイマー情報を表示することをユーザーに許可します。
