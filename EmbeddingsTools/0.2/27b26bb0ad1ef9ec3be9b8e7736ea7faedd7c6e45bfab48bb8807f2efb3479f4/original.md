```
subspace(emb::AbstractEmbedding, tokens::Vector{String})::WordEmbedding
```

The `subspace()` function takes an existing embedding and a subset of its vocabulary as input and creates a new `WordEmbedding` object. The order of embedding vectors in the new embedding corresponds to the order of input `tokens`. If a token is not found in the source embedding vocabulary, a zero vector is returned for that token. 

It's worth noting that this method is relatively slow and doesn't assume the source embedding to be indexed. Therefore, it doesn't take advantage of a lookup dictionary. It's recommended to index an embedding before subsetting it for better performance.
