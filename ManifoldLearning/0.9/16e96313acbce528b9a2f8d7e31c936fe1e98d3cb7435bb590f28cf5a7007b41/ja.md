```
fit(Isomap, data; k=12, maxoutdim=2, nntype=BruteForce)
```

`data`にアイソメトリックマッピングモデルをフィットさせます。

# 引数

  * `data`: 観測の行列。`data`の各列は1つの観測です。

# キーワード引数

  * `k`: ローカルサブスペース表現の構築のための最近傍の数
  * `maxoutdim`: 縮小された空間の次元。
  * `nntype`: 最近傍構築クラス（`AbstractNearestNeighbors`から派生）

# 例

```julia
M = fit(Isomap, rand(3,100)) # Isomapモデルを構築
R = predict(M)               # 次元削減を実行
```
