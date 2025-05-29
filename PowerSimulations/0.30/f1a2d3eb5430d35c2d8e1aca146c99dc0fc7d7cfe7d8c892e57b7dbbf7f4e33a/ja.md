空のエミュレーションモデルを構築します。このコンストラクタは、テンプレートを必要としないカスタムエミュレーションモデルの実装に使用されます。

# 引数

  * `::Type{M} where M<:EmulationProblem`: 抽象操作モデルのタイプ
  * `sys::PSY.System`: Power Systemsを使用して作成されたシステム
  * `jump_model::Union{Nothing, JuMP.Model}` = nothing: カスタムJuMPモデルを渡すことを可能にします。注意して使用してください。

# 例

```julia
problem = EmulationModel(system, optimizer)
```
