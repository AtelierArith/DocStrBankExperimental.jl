```
get_embeddings(embedder::BitPackedBatchEmbedder, docs::AbstractVector{<:AbstractString};
	verbose::Bool = true,
	model::AbstractString = PT.MODEL_EMBEDDING,
	truncate_dimension::Union{Int, Nothing} = nothing,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	target_batch_size_length::Int = 80_000,
	ntasks::Int = 4 * Threads.nthreads(),
	kwargs...)
```

提供されたモデル（キーワード引数 `model`）を使用して、`docs` のベクトルをバッチ方式で埋め込み、その後、UInt64（ビットパック）で表されたバイナリ埋め込み行列 - `BitPackedBatchEmbedder` を返します。

`BitPackedBatchEmbedder` は、ネットワークのレイテンシを減らすために、APIのレート制限を超えないように、1回の呼び出しで約80K文字の埋め込み呼び出しをバッチ処理しようとします。

埋め込みの迅速かつメモリ効率の良いストレージのための最良のオプションは、取得に `BitPackedCosineSimilarity` を使用することです。

# 注意事項

  * `docs` は、埋め込みコンテキスト制限内に収まる合理的なサイズにすでにチャンク化されていると仮定されています。
  * 入力サイズを超えるエラーが発生した場合は、最初にチャンク内の `max_length` を確認してください。それでも問題が解決しない場合は、`target_batch_size_length` パラメータ（例：10_000）とタスク数 `ntasks=1` を減らしてみてください。一部のプロバイダーは大きなバッチサイズを処理できません。

# 引数

  * `docs`: 埋め込む文字列のベクトル。
  * `verbose`: 詳細出力のためのブールフラグ。デフォルトは `true`。
  * `model`: 埋め込みに使用するモデル。デフォルトは `PT.MODEL_EMBEDDING`。
  * `truncate_dimension`: 切り捨てる埋め込みの次元数。デフォルトは `nothing`。
  * `cost_tracker`: API呼び出しの総コストを追跡するための `Threads.Atomic{Float64}` オブジェクト。親呼び出しに総コストを渡すのに便利です。
  * `target_batch_size_length`: 埋め込みのために送信される各ドキュメントチャンクのバッチのターゲット長（文字数）。デフォルトは80_000文字。埋め込みプロセスを高速化します。
  * `ntasks`: asyncmapに使用するタスクの数。デフォルトは 4 * Threads.nthreads()。

関連情報: `unpack_bits`, `pack_bits`, `BitPackedCosineSimilarity`。
