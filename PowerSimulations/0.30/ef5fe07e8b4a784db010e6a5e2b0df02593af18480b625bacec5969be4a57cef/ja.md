空の意思決定モデルを構築します。このコンストラクタは、テンプレートを必要としないカスタム意思決定モデルの実装に使用されます。

# 引数

  * `::Type{M} where M<:DecisionProblem`: 抽象操作モデルの型
  * `sys::PSY.System`: Power Systemsを使用して作成されたシステム
  * `jump_model::Union{Nothing, JuMP.Model}` = nothing: カスタムJuMPモデルを渡すことを可能にします。注意して使用してください。

# 例

```julia
problem = DecisionModel(system, optimizer)
```
