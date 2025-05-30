```
write_embedding(
    emb::WordEmbedding,
    path::AbstractString;
    max_vocab_size::Union{Int,Nothing}=nothing,
    keep_words::Union{Vector{String},Nothing}=nothing
)::Nothing
```

`write_embedding()` 関数は、指定された `path` にバイナリファイルとして `WordEmbedding` オブジェクトを保存します。語彙は `keep_words` でフィルタリングでき、`max_vocab_size` に制限できます。
