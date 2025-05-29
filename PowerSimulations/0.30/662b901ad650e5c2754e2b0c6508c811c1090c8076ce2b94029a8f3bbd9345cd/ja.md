```julia
build!(
    model::PowerSimulations.DecisionModel;
    output_dir,
    recorders,
    console_level,
    file_level,
    disable_timer_outputs
)

```

指定されたDecisionProblemに基づいてDecision Modelを構築します。

# 引数

  * `model::DecisionModel{<:DecisionProblem}`: DecisionModelオブジェクト
  * `output_dir::String`: 結果の出力ディレクトリ
  * `recorders::Vector{Symbol} = []`: 登録するレコーダー名
  * `console_level = Logging.Error`:
  * `file_level = Logging.Info`:
  * `disable_timer_outputs = false` : タイミング出力の有効/無効
