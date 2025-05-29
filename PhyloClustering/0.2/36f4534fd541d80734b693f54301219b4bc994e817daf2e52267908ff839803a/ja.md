```
plot_clusters(tree::AbstractMatrix{<:Real}, label::Vector{Int64})
```

モデルの結果を視覚化します。

# 引数

  * `tree`: B * N のツリーマトリックス（ツリーマトリックスの各列は二分割形式のB次元ツリーです）。
  * `label`: 各ツリーの予測ラベルを含むN長のベクター。人々はモデルの出力を使用できます。

# 出力

ツリークラスタを示す散布図。
