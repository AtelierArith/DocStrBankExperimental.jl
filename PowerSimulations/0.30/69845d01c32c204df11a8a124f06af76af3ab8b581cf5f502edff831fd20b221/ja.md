```
SimulationModels(
    decision_models::Vector{<:DecisionModel},
    emulation_models::Union{Nothing, EmulationModel}
)
```

シミュレーションで使用するOperationProblemの定義を格納します。SimulationModelsを作成する際、モデルが作成される順序がシミュレーションの実行順序を決定します。

# 引数

  * `decision_models::Vector{<:DecisionModel}`: 意思決定モデルのベクター。
  * `emulation_models::Union{Nothing, EmulationModel}`: シミュレーションにEmulationModelを含めるためのオプション引数。

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
```
