```
rephrase(rephraser::SimpleRephraser, question::AbstractString;
	verbose::Bool = true,
	model::String = PT.MODEL_CHAT, template::Symbol = :RAGQueryHyDE,
	cost_tracker = Threads.Atomic{Float64}(0.0))
```

`question`を提供されたリフレイザー`template = RAGQueryHyDE`を使用して言い換えます。

HyDE（Hypothetical Document Embedding）メソッドを使用した特別な言い換えのフレーバーで、私たちの質問に対する良い答えとなる合成パッセージに最も類似した文書を見つけることを目的としています。

元の質問とリフレーズされた質問の両方を返します。

# 引数

  * `rephraser`: 言い換えステップのロジックを決定するタイプ。
  * `question`: 言い換えられる質問。
  * `model`: 言い換えに使用するモデル。デフォルトは`PT.MODEL_CHAT`。
  * `template`: 使用する言い換えテンプレート。デフォルトは`:RAGQueryHyDE`。`aitemplates("rephrase")`でさらに見つけることができます。
  * `verbose`: 詳細なログを印刷するかどうかを示すブールフラグ。デフォルトは`true`。
