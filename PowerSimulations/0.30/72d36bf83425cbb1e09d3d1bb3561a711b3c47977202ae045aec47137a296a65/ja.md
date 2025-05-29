```julia
DecisionModel(
    ::Type{M<:PowerSimulations.DecisionProblem},
    template::PowerSimulations.AbstractProblemTemplate,
    sys::PowerSystems.System;
    ...
) -> PowerSimulations.DecisionModel
DecisionModel(
    ::Type{M<:PowerSimulations.DecisionProblem},
    template::PowerSimulations.AbstractProblemTemplate,
    sys::PowerSystems.System,
    jump_model::Union{Nothing, JuMP.Model};
    kwargs...
) -> PowerSimulations.DecisionModel

```

特定のシステムとテンプレートを使用して、タイプ M の最適化問題を構築します。

# 引数

  * `::Type{M} where M<:DecisionProblem`: 抽象操作モデルタイプ
  * `template::AbstractProblemTemplate`: 送電、デバイス、ブランチ、およびサービスで構成されるモデル参照。
  * `sys::PSY.System`: Power Systems を使用して作成されたシステム
  * `jump_model::Union{Nothing, JuMP.Model}` = nothing: カスタム JuMP モデルを渡すことを可能にします。注意して使用してください。

# 例

```julia
template = ProblemTemplate(CopperPlatePowerModel, devices, branches, services)
problem = DecisionModel(MyOpProblemType, template, system, optimizer)
```
