```
simplenicheAE(numniches::Int64, dimension::Tuple,
                    maxBud::Float64, area::Unitful.Area{Float64},
                    active::Matrix{Bool})
```

`DiscreteHab`、`SimpleBudget` タイプの非生物的環境を作成する関数です。ニッチタイプの数 `numniches` が与えられると、指定された面積 `area` と次元 `dimension` を持つ `DiscreteHab` 環境が作成されます。また、最大予算値 `maxbud` で満たされた `SimpleBudget` タイプも作成されます。アクティブなグリッドセルの Bool 行列 `active` が含まれている場合はこれが使用され、そうでない場合はすべてのグリッドセルがアクティブなものが作成されます。
