```
reduce_emb(emb::IndexedWordEmbedding, k::Integer; method::String="pca")::WordEmbedding
```

The following function takes an existing indexed word embedding and reduces its embedding vectors to a specified number of dimensions `k`. The function returns a new IndexedWordEmbedding object. You can choose between two reduction techniques by setting the `method` parameter to either `pca` for Principal Component Analysis or `svd` for Singular Value Decomposition.
