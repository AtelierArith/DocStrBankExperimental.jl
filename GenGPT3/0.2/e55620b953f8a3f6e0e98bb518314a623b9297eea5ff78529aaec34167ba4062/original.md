```
findsimilar(store::EmbeddingStore, text, k; reversed=false)
findsimilar(store::EmbeddingStore, embedding, k; reversed=false)
```

Returns the `k` most similar entries to the `text` or `embedding` in the `EmbeddingStore`. If `reversed` is `true`, entries are returned in order of increasing similarity.
