```
scattermat(X, [wv::AbstractWeights]; mean=nothing, dims=1)
```

散布行列を計算します。これは非正規化共分散行列です。重み付けベクトル `wv` を指定して推定値に重みを付けることができます。

# 引数

  * `mean=nothing`: 知られている平均値。`nothing` は平均が不明であることを示し、関数は平均を計算します。`mean=0` を指定すると、データが中心化されていることを示し、平均を引く必要がないことになります。
  * `dims=1`: 変数が整理される次元。`dims = 1` の場合、変数は列として扱われ、観測値は行にあります。`dims = 2` の場合、変数は行として扱われ、観測値は列にあります。
