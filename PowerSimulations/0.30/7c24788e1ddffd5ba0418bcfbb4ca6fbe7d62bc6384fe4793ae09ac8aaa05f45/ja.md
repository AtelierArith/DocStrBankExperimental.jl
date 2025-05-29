```
Simulation(
    sequence::SimulationSequence,
    name::String,
    steps::Int
    models::SimulationModels,
    simulation_folder::String,
    initial_time::Union{Nothing, Dates.DateTime}
)
```

`Simulation` 構造体を構築して、指定された意思決定およびエミュレーションモデルのシーケンスを実行します。

# 引数

  * `sequence::SimulationSequence`: 意思決定およびエミュレーションモデルがどのように実行されるかを指定するシミュレーションシーケンス。
  * `name::String`: シミュレーションの名前
  * `steps::Int`: モデルのシーケンスが実行されるステップ数
  * `models::SimulationModels`: 意思決定およびエミュレーションモデルのリスト
  * `simulation_folder::String`: 結果が保存されるフォルダー
  * `initial_time::Union{Nothing, Dates.DateTime} = nothing`: シミュレーションが開始される初期時間。何も指定しない場合、システムの時系列の最初のタイムスタンプがデフォルトとなります。

# 例

```julia
template_uc = template_unit_commitment()
template_ed = template_economic_dispatch()
my_decision_model_uc = DecisionModel(template_1, sys_uc, optimizer, name = "UC")
my_decision_model_ed = DecisionModel(template_ed, sys_ed, optimizer, name = "ED")
models = SimulationModels(
    decision_models = [
        my_decision_model_uc,
        my_decision_model_ed
    ]
)
# 次のシーケンスは、UCからEDへの `ThermalStandard` ユニットのコミットメント変数（`OnVariable`）を設定します。
sequence = SimulationSequence(;
    models = models,
    feedforwards = Dict(
        "ED" => [
            SemiContinuousFeedforward(;
                component_type = ThermalStandard,
                source = OnVariable,
                affected_values = [ActivePowerVariable],
            ),
        ],
    ),
)

sim = Simulation(
    sequence = sequence,
    name = "Sim",
    steps = 5,
    models = models,
    simulation_folder = mktempdir(cleanup=true),
)
```
