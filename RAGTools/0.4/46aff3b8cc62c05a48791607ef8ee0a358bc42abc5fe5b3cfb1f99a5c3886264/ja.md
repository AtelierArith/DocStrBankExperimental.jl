```
get_keywords(
	processor::KeywordsProcessor, docs::AbstractVector{<:AbstractString};
	verbose::Bool = true,
	stemmer = nothing,
	stopwords::Set{String} = Set(STOPWORDS),
	return_keywords::Bool = false,
	min_length::Integer = 3,
	min_term_freq::Int = 1, max_terms::Int = typemax(Int),
	kwargs...)
```

`docs`のベクトルから提供された`stemmer`と`stopwords`を使用して`DocumentTermMatrix`を生成します。

# 引数

  * `docs`: 埋め込む文字列のベクトル。
  * `verbose`: 詳細出力のためのブールフラグ。デフォルトは`true`。
  * `stemmer`: ステミングに使用するステマー。デフォルトは`nothing`。
  * `stopwords`: 削除するストップワードのセット。デフォルトは`Set(STOPWORDS)`。
  * `return_keywords`: キーワードを返すためのブールフラグ。デフォルトは`false`。検索時のクエリ処理に便利。
  * `min_length`: キーワードの最小長。デフォルトは`3`。
  * `min_term_freq`: 語彙に含めるために用語が持つ必要がある最小頻度。例えば、`min_term_freq = 2`は、少なくとも2回出現する用語のみが含まれることを意味します。
  * `max_terms`: 語彙に含める最大用語数。例えば、`max_terms = 100`は、最も頻繁に出現する100の用語のみが含まれることを意味します。
