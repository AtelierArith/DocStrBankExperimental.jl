```
pca_reduction(wv::WordVectors, rdim=7, outdim=size(wv.vectors,1); [do_pca=true])
```

単語埋め込み `wv` を後処理し、単語ベクトルから最初の `rdim` PCA コンポーネントを削除し、さらに `do_pca=true` の場合は、次の PCA 変換を通じて次元を `outdim` に削減します。

# 引数

  * `wv::WordVectors` 単語埋め込み
  * `rdim::Int` データから削除する PCA コンポーネントの数 (デフォルト 7)
  * `outdim::Int` PCA 次元削減後のデータの出力次元; `do_pca=true` の場合のみ実行され、デフォルト値は入力埋め込みの値と同じで、すなわち削減は行われません

# キーワード引数

  * `do_pca::Bool` 後処理されたデータの PCA 変換を実行するかどうか (デフォルト `true`)

# 参考文献:

  * [Vikas Raunak "Simple and effective dimensionality reduction for  word embeddings", NIPS 2017 Workshop](https://arxiv.org/abs/1708.03629)
