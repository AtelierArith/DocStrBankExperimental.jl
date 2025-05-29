```
EmbedResult{T <: Real}
```

埋め込みパッセージの結果。

# フィールド

  * `embeddings::AbstractArray{T}`: パッセージの埋め込み。プロパティ `embeddings` はサイズ `(batch_size, embedding_dimension)` の列優先行列です。
  * `elapsed::Float64`: パッセージを埋め込むのにかかった時間。
