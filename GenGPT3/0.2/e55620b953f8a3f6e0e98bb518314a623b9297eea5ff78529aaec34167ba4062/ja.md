```
findsimilar(store::EmbeddingStore, text, k; reversed=false)
findsimilar(store::EmbeddingStore, embedding, k; reversed=false)
```

`EmbeddingStore`内の`text`または`embedding`に最も類似した`k`件のエントリを返します。`reversed`が`true`の場合、エントリは類似度が低い順に返されます。
