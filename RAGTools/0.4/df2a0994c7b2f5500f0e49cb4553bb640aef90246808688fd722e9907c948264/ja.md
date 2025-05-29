```
annotate_support(annotater::TrigramAnnotater, answer::AbstractString,
	context::AbstractVector; min_score::Float64 = 0.5,
	skip_trigrams::Bool = true, hashed::Bool = true,
	sources::Union{Nothing, AbstractVector{<:AbstractString}} = nothing,
	min_source_score::Float64 = 0.25,
	add_sources::Bool = true,
	add_scores::Bool = true, kwargs...)
```

`answer`を`context`でサポートされている部分で注釈を付け、`answer`を表すノードの注釈付きツリーを返します。

"root"ノードを返し、子ノードは`answer`内の文やコードブロックを表します。重複を避けるために、"leaf"ノードのみが印刷されます。"leaf"ノードとは、子を持たないノードのことです。

デフォルトのロジック:

  * 文やコードブロックに分割し、次にトークン（~単語）に分割します。
  * その後、各トークン（~単語）を正確に一致させます。
  * 正確な一致が見つからない場合、トライグラムベースの一致をカウントします（より良い文脈認識のために周囲のトークンを含めます）。
  * 一致が`min_score`を超える場合、ノードの`score`に記録されます。

# 引数

  * `annotater::TrigramAnnotater`: 使用するアノテーター
  * `answer::AbstractString`: 注釈を付けるテキスト
  * `context::AbstractVector`: 注釈を付けるためのコンテキスト、つまり、`context`内のテキストで"サポート"を探します
  * `min_score::Float64`: 一致と見なすための最小スコア。デフォルト: 0.5、これは各単語のトライグラムの半分が一致する必要があることを意味します
  * `skip_trigrams::Bool`: 正確な完全一致が見つかった場合にトライグラムの一致をスキップするかどうか。デフォルト: true
  * `hashed::Bool`: ハッシュ化されたトライグラムを使用するかどうか。デバッグが難しくなりますが、大きなテキストに対してははるかに高速です（ハッシュ化されたテキストは重複を排除するためにSetに保持されます）。デフォルト: true
  * `sources::Union{Nothing, AbstractVector{<:AbstractString}}`: コンテキストの最後に追加するソース。デフォルト: nothing
  * `min_source_score::Float64`: ソースを考慮/表示するための最小スコア。デフォルト: 0.25、これは各単語のトライグラムの少なくとも4分の1が何らかのコンテキストと一致する必要があることを意味します。この閾値は`min_score`よりも低く、ブロック内のすべての単語に対する平均であるため、生成されたテキストと完全に一致するのははるかに難しいです。
  * `add_sources::Bool`: 各コードブロック/文の最後にソースを追加するかどうか。ソースは"[1]"のように角括弧内に追加されます。デフォルト: true
  * `add_scores::Bool`: 各コードブロック/文の最後にソース一致スコアを追加するかどうか。スコアは"[0.75]"のように角括弧内に追加されます。デフォルト: true
  * kwargs: `trigram_support!`および`set_node_style!`に渡す追加のキーワード引数。詳細については、それらのドキュメントを参照してください（例: スコアに基づいてノードの色をカスタマイズする）

# 例

```julia
annotater = TrigramAnnotater()
context = [
	"This is a test context.", "Another context sentence.", "Final piece of context."]
answer = "This is a test context. Another context sentence."

annotated_root = annotate_support(annotater, answer, context)
pprint(annotated_root) # 注釈付きツリーをきれいに印刷
```
