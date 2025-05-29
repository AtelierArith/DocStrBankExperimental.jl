```
rephrase(rephraser::SimpleRephraser, question::AbstractString;
	verbose::Bool = true,
	model::String = PT.MODEL_CHAT, template::Symbol = :RAGQueryOptimizer,
	cost_tracker = Threads.Atomic{Float64}(0.0), kwargs...)
```

`question`を提供されたリフレイザー`template`を使用して言い換えます。

元の質問と言い換えた質問の両方を返します。

# 引数

  * `rephraser`: 言い換えステップのロジックを決定するタイプ。
  * `question`: 言い換えられる質問。
  * `model`: 言い換えに使用するモデル。デフォルトは`PT.MODEL_CHAT`です。
  * `template`: 使用する言い換えテンプレート。デフォルトは`:RAGQueryOptimizer`です。`aitemplates("rephrase")`でさらに見つけることができます。
  * `verbose`: 詳細なログを印刷するかどうかを示すブールフラグ。デフォルトは`true`です。
