```
fit(LTSA, data; k=12, maxoutdim=2, nntype=BruteForce)
```

`data`にローカル接線空間整列モデルをフィットさせます。

# 引数

  * `data`: 観測の行列。`data`の各列は1つの観測です。

# キーワード引数

  * `k`: ローカル部分空間表現の構築に使用する最近傍の数
  * `maxoutdim`: 縮小された空間の次元。
  * `nntype`: 最近傍構築クラス（`AbstractNearestNeighbors`から派生）

# 例

```julia
M = fit(LTSA, rand(3,100)) # LTSAモデルを構築
R = transform(M)           # 次元削減を実行
```
