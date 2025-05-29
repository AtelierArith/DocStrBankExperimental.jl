```
fit(LEM, data; k=12, maxoutdim=2, ɛ=1.0, nntype=BruteForce)
```

`data`にラプラシアン固有写像モデルをフィットさせます。

# 引数

  * `data`: 観測の行列。`data`の各列は1つの観測です。

# キーワード引数

  * `k`: ローカル部分空間表現の構築のための最近傍数
  * `maxoutdim`: 符号化された空間の次元。
  * `nntype`: 最近傍構築クラス（`AbstractNearestNeighbors`から派生）
  * `ɛ`: ガウスカーネルの分散（スケールパラメータ）
  * `laplacian`: スペクトル分解に使用されるラプラシアン行列の形式

      * `:unnorm`: 非正規化ラプラシアン
      * `:sym`: 対称正規化ラプラシアン
      * `:rw`: ランダムウォーク正規化ラプラシアン

# 例

```julia
M = fit(LEM, rand(3,100)) # ラプラシアン固有写像モデルを構築
R = predict(M)          # 次元削減を実行
```
