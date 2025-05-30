```
subspace(emb::IndexedWordEmbedding, tokens::Vector{String})::WordEmbedding
```

The `subspace()` function takes an already indexed embedding and a subset of its vocabulary as input and generates a new `WordEmbedding` object. It requires two arguments: `emb` which is the indexed embedding, and `tokens` which is a vector of strings representing the subset of vocabulary.

The order of embedding vectors in the new embedding corresponds to the order of the input `tokens`. If an out-of-vocabulary token is encountered, a zero vector is returned.

This method assumes that the source embedding is indexed and can use its lookup dictionary, making it relatively fast. It is recommended to `index()` an embedding before subsetting it.

Note that the output of the `subspace()` function is not an indexed embedding. So, if the user wants it indexed, it needs to be done manually.
