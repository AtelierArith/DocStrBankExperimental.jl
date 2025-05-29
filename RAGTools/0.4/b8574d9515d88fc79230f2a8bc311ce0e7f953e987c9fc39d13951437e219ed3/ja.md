```
get_embeddings(embedder::BinaryBatchEmbedder, docs::AbstractVector{<:AbstractString};
	verbose::Bool = true,
	model::AbstractString = PT.MODEL_EMBEDDING,
	truncate_dimension::Union{Int, Nothing} = nothing,
	return_type::Type = Matrix{Bool},
	cost_tracker = Threads.Atomic{Float64}(0.0),
	target_batch_size_length::Int = 80_000,
	ntasks::Int = 4 * Threads.nthreads(),
	kwargs...)
```

提供されたモデル（キーワード引数 `model`）を使用して、`docs` のベクトルをバッチ方式で埋め込み、その後バイナリ埋め込み行列 - `BinaryBatchEmbedder` を返します。

`BinaryBatchEmbedder` は、ネットワークのレイテンシを減らすために、APIのレート制限を超えないように、1回の呼び出しで約80K文字の埋め込み呼び出しをバッチ処理しようとします。

# 注意事項

  * `docs` は、埋め込みコンテキスト制限内に収まる合理的なサイズにすでにチャンク化されていると仮定されます。
  * 入力サイズを超えるエラーが発生した場合は、まずチャンク内の `max_length` を確認してください。それでも問題が解決しない場合は、`target_batch_size_length` パラメータ（例：10_000）とタスク数 `ntasks=1` を減らしてみてください。一部のプロバイダーは大きなバッチサイズを処理できません。

# 引数

  * `docs`: 埋め込む文字列のベクトル。
  * `verbose`: 詳細出力のためのブールフラグ。デフォルトは `true`。
  * `model`: 埋め込みに使用するモデル。デフォルトは `PT.MODEL_EMBEDDING`。
  * `truncate_dimension`: 切り捨てる埋め込みの次元数。デフォルトは `nothing`。
  * `return_type`: 返される埋め込み行列の型。デフォルトは `Matrix{Bool}`。ストレージ要件を最小限に抑えるために `BitMatrix` を選択し、要素ごとの操作のパフォーマンスを最大化するために `Matrix{Bool}` を選択します。
  * `cost_tracker`: API呼び出しの総コストを追跡するための `Threads.Atomic{Float64}` オブジェクト。親呼び出しに総コストを渡すのに便利です。
  * `target_batch_size_length`: 埋め込みのために送信される各ドキュメントチャンクのバッチのターゲット長（文字数）。デフォルトは80_000文字。埋め込みプロセスを高速化します。
  * `ntasks`: asyncmapに使用するタスクの数。デフォルトは 4 * Threads.nthreads()。
