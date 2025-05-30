```
fit(LLE, data; k=12, maxoutdim=2, nntype=BruteForce, tol=1e-5)
```

`data`に対して局所線形埋め込みモデルを適合させます。

# 引数

  * `data`: 観測の行列。`data`の各列は1つの観測です。

# キーワード引数

  * `k`: 局所部分空間表現の構築のための最近傍の数
  * `maxoutdim`: 縮小された空間の次元。
  * `nntype`: 最近傍構築クラス（`AbstractNearestNeighbors`から派生）
  * `tol`: アルゴリズムの正則化許容値

# 例

```julia
M = fit(LLE, rand(3,100)) # LLEモデルを構築
R = transform(M)          # 次元削減を実行
```
