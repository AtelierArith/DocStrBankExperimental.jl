```
run_qa_evals(qa_item::QAEvalItem, ctx::RAGResult; verbose::Bool = true,
			 parameters_dict::Dict{Symbol, <:Any}, judge_template::Symbol = :RAGJudgeAnswerFromContext,
			 model_judge::AbstractString, api_kwargs::NamedTuple = NamedTuple()) -> QAEvalResult
```

単一の `QAEvalItem` を RAG の詳細 (`RAGResult`) を使用して評価し、`QAEvalResult` 構造体を返します。この関数は、QA 評価コンテキストで生成された回答の関連性と正確性を評価します。

# 引数

  * `qa_item::QAEvalItem`: 質問とその回答を含む QA 評価アイテム。
  * `ctx::RAGResult`: QA ペアを生成するために使用される RAG 結果で、元のコンテキストと回答が含まれています。`airag(...; return_context=true)` から取得されます。
  * `verbose::Bool`: `true` の場合、詳細なログを有効にします。デフォルトは `true` です。
  * `parameters_dict::Dict{Symbol, Any}`: 後の評価のために使用されるパラメータを追跡します。キーはシンボルでなければなりません。
  * `judge_template::Symbol`: 回答を判断するために使用される AI モデルのテンプレートシンボル。デフォルトは `:RAGJudgeAnswerFromContext` です。
  * `model_judge::AbstractString`: 回答の質を判断するために使用される AI モデル。デフォルトは標準のチャットモデルですが、より強力なモデルである GPT-4 を使用することをお勧めします。
  * `api_kwargs::NamedTuple`: API エンドポイントに転送されるパラメータ。

# 戻り値

`QAEvalResult`: QA 評価に関連するさまざまなスコアとメタデータを含む評価結果。

# 注意事項

  * この関数は、コンテキストが QA コンテキストとどれだけ一致しているかに基づいて、取得スコアとランクを計算します。
  * 次に、`judge_template` と `model_judge` を使用して、回答の正確性と関連性をスコアリングします。
  * 評価中にエラーが発生した場合、関数は警告をログに記録し（`verbose` が `true` の場合）、`answer_score` は `nothing` に設定されます。

# 例

特定のコンテキストとモデルを使用して QA ペアを評価する:

```julia
qa_item = QAEvalItem(question="フランスの首都はどこですか？", answer="パリ", context="フランスはヨーロッパの国です。")
ctx = RAGResult(source="Wikipedia", context="フランスはヨーロッパの国です。", answer="パリ")
parameters_dict = Dict("param1" => "value1", "param2" => "value2")

eval_result = run_qa_evals(qa_item, ctx, parameters_dict=parameters_dict, model_judge="MyAIJudgeModel")
```
