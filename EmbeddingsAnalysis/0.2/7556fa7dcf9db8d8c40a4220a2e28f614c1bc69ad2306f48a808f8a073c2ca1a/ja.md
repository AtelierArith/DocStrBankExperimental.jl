```
cosine_vec(wv::WordVectors, wordvector, n=10 [;vocab=nothing])
```

コサイン類似度を計算し、`wordvector` と `wv` の単語ベクトルとの間の最良の `n` の位置と計算された値を返します。語彙マスク `vocab` を指定することで、単語ベクトルのサブセットのみを考慮することができます。
