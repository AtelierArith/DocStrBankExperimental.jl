```
get_vector(emb::IndexedWordEmbedding, query::String)
```

`get_vector()` returns embedding vector (Float32) for a given token `query`. Called with the embedding object rather than with the dictionary. Type-stable: returns a view of the embedding vector or throws an exception.
