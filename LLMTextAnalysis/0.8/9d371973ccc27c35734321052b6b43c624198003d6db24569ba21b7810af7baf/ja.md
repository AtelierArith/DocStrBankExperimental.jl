```
TopicMetadata <: AbstractTopicMetadata
```

特定のトピックのメタデータを、文書のコレクションから抽出した構造体です。

# フィールド

  * `index_id::Symbol`: トピックの識別子。
  * `topic_level::Union{AbstractString, Int}`: 階層におけるトピックのレベル。
  * `topic_idx::Int`: トピックのインデックス。
  * `label::AbstractString`: トピックの人間が読めるラベル。デフォルトは `""`。
  * `summary::AbstractString`: トピックの簡潔な要約。デフォルトは `""`。
  * `docs_idx::Vector{Int}`: このトピックに属する文書のインデックス。`index.docs`内の位置に対応します。
  * `center_doc_idx::Int`: このトピックの中心文書のインデックス。`docs_idx`内の位置に対応します（インデックスではありません！）
  * `samples_doc_idx::Vector{Int}`: 代表的な文書のインデックス。`docs_idx`内の位置に対応します（インデックスではありません！）
  * `keywords_idx::Vector{Int}`: このトピックに関連する特定のキーワードのインデックス。`index.keywords_vocab`内の位置に対応します。

# 例

```julia
topic = TopicMetadata(topic_level=1, topic_idx=5)
```
