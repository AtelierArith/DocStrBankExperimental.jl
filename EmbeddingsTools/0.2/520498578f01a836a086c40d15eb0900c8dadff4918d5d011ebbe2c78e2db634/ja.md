```
reduce_emb(emb::AbstractEmbedding, k::Integer; method::String="pca")::WordEmbedding
```

次の関数は、既存の単語埋め込みを取得し、その埋め込みベクトルを指定された次元数 `k` に削減します。この関数は、新しい WordEmbedding オブジェクトを返します。`method` パラメータを `pca`（主成分分析）または `svd`（特異値分解）のいずれかに設定することで、2つの削減技術のいずれかを選択できます。
