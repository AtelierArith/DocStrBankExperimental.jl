```
get_tags(tagger::OpenTagger, docs::AbstractVector{<:AbstractString};
	verbose::Bool = true,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...)
```

指定されたモデル（キーワード引数 `model`）を使用して、`docs` のベクトルから「タグ」（メタデータ/キーワード）を抽出します。

# 引数

  * `docs`: 埋め込むための文字列のベクトル。
  * `verbose`: 詳細出力のためのブールフラグ。デフォルトは `true`。
  * `model`: タグ抽出に使用するモデル。デフォルトは `PT.MODEL_CHAT`。
  * `template`: タグ抽出に使用するテンプレート。デフォルトは `:RAGExtractMetadataShort`。
  * `cost_tracker`: API呼び出しの総コストを追跡するための `Threads.Atomic{Float64}` オブジェクト。親呼び出しに総コストを渡すのに便利です。
