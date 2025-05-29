```
SubChunkIndex
```

`chunks`（およびチャンクに整列したフィールド）に関する親インデックスのビュー。`AbstractChunkIndex`に対して機能するすべてのメソッドとアクセサは、`SubChunkIndex`にも適用されます。`MultiIndex`にはまだ対応していません。

# フィールド

  * `parent::AbstractChunkIndex`: チャンクが抽出される親インデックス（常に元のインデックスであり、ビューではありません）
  * `positions::Vector{Int}`: 親インデックスにおけるチャンクの位置（常に元のPARENTインデックスを参照し、ビューのビューを作成しても変わりません）

# 例

```julia
cc = CandidateChunks(index.id, 1:10)
sub_index = @view(index[cc])
```

`SubChunkIndex`を使用して、親インデックスからチャンクやソース（および他のフィールド）にアクセスできます。例えば、

```julia
RT.chunks(sub_index)
RT.sources(sub_index)
RT.chunkdata(sub_index) # 埋め込みのスライス
RT.embeddings(sub_index) # 埋め込みのスライス
RT.tags(sub_index) # タグのスライス
RT.tags_vocab(sub_index) # 変更なし、親バージョンと同一
RT.extras(sub_index) # エクストラのスライス
```

`positions`が対応する親インデックスにアクセスします。

```julia
parent(sub_index)
RT.positions(sub_index)
```
