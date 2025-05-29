```
SimulationSequence(
    models::SimulationModels,
    feedforward::Dict{String, Vector{<:AbstractAffectFeedforward}}
    ini_cond_chronology::InitialConditionChronology
)
```

意思決定モデルとエミュレーションモデルの間のシミュレーションシーケンスを構築します。

# 引数

  * `models::SimulationModels`: 意思決定モデルとエミュレーションモデルのベクター。
  * `feedforward = Dict{String, Vector{<:AbstractAffectFeedforward}}()`: 意思決定モデルとエミュレーションモデルの間で情報と変数がどのように交換されるかを指定するオプションの辞書。
  * `ini_cond_chronology::InitialConditionChronology =  InterProblemChronology()`: ステージ間の情報共有モデルを定義します [`InterProblemChronology`](@ref)

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
# 次のシーケンスは、UCからEDへの`ThermalStandard`ユニットのコミットメント変数（`OnVariable`）を設定します。
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
```
