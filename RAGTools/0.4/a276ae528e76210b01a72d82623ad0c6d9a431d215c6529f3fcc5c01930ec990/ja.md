```
ChunkEmbeddingsIndex
```

ドキュメントチャンクとその埋め込みを保存するためのメイン構造体です。また、各チャンクのタグとソースも保存します。

以前は、この構造体は `ChunkIndex` と呼ばれていました。

# フィールド

  * `id::Symbol`: 各インデックスの一意の識別子（`CandidateChunks` で正しいインデックスを使用していることを確認するため）
  * `chunks::Vector{<:AbstractString}`: 基本となるドキュメントチャンク / スニペット
  * `embeddings::Union{Nothing, Matrix{<:Real}}`: セマンティック検索用
  * `tags::Union{Nothing, AbstractMatrix{<:Bool}}`: 正確な検索、フィルタリングなどのため。これはしばしばスパース行列で、与えられた `tag` を持つチャンクを示します（位置のルックアップについては `tag_vocab` を参照）
  * `tags_vocab::Union{Nothing, Vector{<:AbstractString}}`: `tags` 行列の語彙（`tags` の各列は `tags_vocab` の1つのアイテムで、行はチャンクです）
  * `sources::Vector{<:AbstractString}`: チャンクのソース
  * `extras::Union{Nothing, AbstractVector}`: 追加データ、例えばメタデータ、ソースコードなど。
