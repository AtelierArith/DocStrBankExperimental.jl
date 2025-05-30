```
index(index_path::String, bert::HF.HGFBertModel, linear::Layers.Dense,
    tokenizer::TextEncoders.AbstractTransformerTextEncoder,
    collection::Vector{String}, dim::Int, index_bsize::Int,
    doc_token::String, skiplist::Vector{Int}, num_chunks::Int,
    chunksize::Int, centroids::AbstractMatrix{Float32},
    bucket_cutoffs::AbstractVector{Float32}, nbits::Int)
```

コレクションのためにインデックスを構築します。

ドキュメントは、サイズ `chunksize` のバッチで処理されます（[`setup`](@ref)を参照）。各バッチの埋め込みとドキュメントの長さが計算され、関連するメタデータと共にディスクに保存されます（[`save_chunk`](@ref)を参照）。

# 引数

  * `index_path`: インデックスを保存するパス。
  * `bert`: ColBERTモデルの事前学習済みBERTコンポーネント。
  * `linear`: ColBERTモデルの事前学習済み線形コンポーネント。
  * `tokenizer`: 使用するトークナイザー。
  * `collection`: インデックスを作成するコレクション。
  * `dim`: 埋め込み次元。
  * `index_bsize`: トランスフォーマーを実行するために使用されるバッチサイズ。
  * `doc_token`: ドキュメントトークン。
  * `skiplist`: スキップするトークンのリスト。
  * `num_chunks`: チャンクの総数。
  * `chunksize`: チャンクの最大サイズ。
  * `centroids`: 圧縮表現を計算するために使用されるセントロイド。
  * `bucket_cutoffs`: 残差を計算するために使用されるカットオフ。
  * `nbits`: 残差をエンコードするビット数。
