```
AbsolutePE{T<:AbstractArray}
AbsolutePE(embedding_size::Int, max_length::Int; base::Number=10_000)
```

絶対位置埋め込みは、「Attention Is All You Need」論文からの正弦波周波数を使用しています。式: PE(pos,2i) = sin(pos/10000^(2i/d*model))         PE(pos,2i+1) = cos(pos/10000^(2i/d*model))

# フィールド

  * `embedding_size::Int`: 埋め込み次元のサイズ (d_model)
  * `max_length::Int`: サポートされる最大シーケンス長
  * `embeddings::T`: 位置埋め込み
