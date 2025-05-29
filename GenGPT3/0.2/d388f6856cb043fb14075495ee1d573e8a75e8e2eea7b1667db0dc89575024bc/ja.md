```
findsimilar(filter_fn::Function,
            store::EmbeddingStore, text, k; reversed=false)
findsimilar(filter_fn::Function,
            store::EmbeddingStore, embedding, k; reversed=false)
```

`filter_fn`でフィルタリングされた後、`EmbeddingStore`内の`text`または`embedding`に最も類似した`k`件のエントリを返します。`reversed`が`true`の場合、エントリは類似度が増加する順に返されます。
