```
DocIndex{T1<:AbstractString, T2<:AbstractMatrix} <: AbstractDocumentIndex
```

文書、埋め込み、および関連情報のインデックスを維持するための構造体です。

# フィールド

  * `id::Symbol`: 文書インデックスの一意の識別子。
  * `docs::Vector{T1}`: 文書のコレクション。
  * `embeddings::Matrix{Float32}`: 文書の埋め込み。文書は列です。
  * `distances::Matrix{Float32}`: 文書埋め込み間のペアワイズ距離。文書は列です。
  * `keywords_ids::T2`: 文書内のキーワードを表すスパース行列。`keywords_vocab`内のキーワードは行、文書は列です。
  * `keywords_vocab::Vector{<:AbstractString}`: キーワードの語彙。
  * `plot_data::Union{Nothing, Matrix{Float32}}`: プロット用の2D埋め込みデータ。行は次元、列は文書です。
  * `clustering::Any`: 文書のクラスタリング結果。
  * `topic_levels::Dict{Union{AbstractString, Int}, Vector{TopicMetadata}}`: 異なるレベルのトピックに関するメタデータ。自動生成された場合は`k` = トピックの数でインデックス付けされ、手動で`build_clusters!`を介して設定された場合は`topic_level`キーワードを介してインデックス付けされます（例：分類器から）。

# 例

```julia
docs = ["Document 1 text", "Document 2 text"]
index = DocIndex(docs=docs, embeddings=rand(Float32, (10, 2)), distances=rand(Float32, (2, 2)))
```
