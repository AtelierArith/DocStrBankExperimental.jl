```
findsimilar(filter_fn::Function,
            store::EmbeddingStore, text, k; reversed=false)
findsimilar(filter_fn::Function,
            store::EmbeddingStore, embedding, k; reversed=false)
```

Returns the `k` most similar entries to the `text` or `embedding` in the `EmbeddingStore` after filtering entries with `filter_fn`. If `reversed` is `true`, entries are returned in order of increasing similarity.
