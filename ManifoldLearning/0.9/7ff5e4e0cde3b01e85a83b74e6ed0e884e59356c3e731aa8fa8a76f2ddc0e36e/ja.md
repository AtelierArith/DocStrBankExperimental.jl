```
fit(HLLE, data; k=12, maxoutdim=2, nntype=BruteForce)
```

`data`にヘッシアン固有写像モデルをフィットさせます。

# 引数

  * `data`: 観測の行列。`data`の各列は1つの観測です。

# キーワード引数

  * `k`: ローカル部分空間表現の構築のための最近傍数
  * `maxoutdim`: 符号化された空間の次元。
  * `nntype`: 最近傍構築クラス（`AbstractNearestNeighbors`から派生）

# 例

```julia
M = fit(HLLE, rand(3,100)) # ヘッシアン固有写像モデルを構築
R = predict(M)             # 次元削減を実行
```
