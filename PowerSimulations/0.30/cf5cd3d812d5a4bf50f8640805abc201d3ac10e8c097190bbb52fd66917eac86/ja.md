```julia
DecisionModel(
    directory::AbstractString,
    optimizer::MathOptInterface.OptimizerWithAttributes;
    jump_model,
    system
) -> Any

```

シリアライズされたファイルからDecisionProblemを構築します。

# 引数

  * `directory::AbstractString`: シリアライズされたモデルを含むディレクトリ
  * `jump_model::Union{Nothing, JuMP.Model}` = nothing: JuMPモデルはシリアライズされません。呼び出し元は元の問題に渡したものを渡す必要があります。
  * `optimizer::Union{Nothing,MOI.OptimizerWithAttributes}` = nothing: オプティマイザはシリアライズされません。呼び出し元は元の問題に渡したものを渡す必要があります。
  * `system::Union{Nothing, PSY.System}`: モデルに使用されるシステム。何も指定しない場合、モデルが作成されたときにsys*to*fileがtrueに設定されていれば、システムはファイルからデシリアライズされます。
