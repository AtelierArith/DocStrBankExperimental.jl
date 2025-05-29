```
run_qa_evals(index::AbstractChunkIndex, qa_items::AbstractVector{<:QAEvalItem};
	api_kwargs::NamedTuple = NamedTuple(),
	airag_kwargs::NamedTuple = NamedTuple(),
	qa_evals_kwargs::NamedTuple = NamedTuple(),
	verbose::Bool = true, parameters_dict::Dict{Symbol, <:Any} = Dict{Symbol, Any}())
```

`QAEvalItem`のベクトルを評価し、`QAEvalResult`のベクトルを返します。この関数は、QA評価コンテキストで生成された回答の関連性と正確性を評価します。

詳細については`?run_qa_evals`を参照してください。

# 引数

  * `qa_items::AbstractVector{<:QAEvalItem}`: 質問とその回答を含むQA評価アイテムのベクトル。
  * `verbose::Bool`: `true`の場合、詳細なログを有効にします。デフォルトは`true`です。
  * `api_kwargs::NamedTuple`: API呼び出しに転送されるパラメータ。詳細については`?aiextract`を参照してください。
  * `airag_kwargs::NamedTuple`: `airag`呼び出しに転送されるパラメータ。詳細については`?airag`を参照してください。
  * `qa_evals_kwargs::NamedTuple`: `run_qa_evals`呼び出しに転送されるパラメータ。詳細については`?run_qa_evals`を参照してください。
  * `parameters_dict::Dict{Symbol, Any}`: 後の評価に使用されるパラメータを追跡します。キーはシンボルでなければなりません。

# 戻り値

`Vector{QAEvalResult}`: QA評価に関連するさまざまなスコアとメタデータを含む評価結果のベクトル。

# 例

```julia
index = "..." # 適切なインデックスが定義されていると仮定
qa_items = [QAEvalItem(question="フランスの首都はどこですか？", answer="パリ", context="フランスはヨーロッパの国です。"),
			QAEvalItem(question="ドイツの首都はどこですか？", answer="ベルリン", context="ドイツはヨーロッパの国です。")]

# `top_k=5`でテストを実行しましょう
results = run_qa_evals(index, qa_items; airag_kwargs=(;top_k=5), parameters_dict=Dict(:top_k => 5))

# "失敗"した呼び出しをフィルタリング
results = filter(x->!isnothing(x.answer_score), results);

# 平均判定スコアを確認
mean(x->x.answer_score, results)
```
