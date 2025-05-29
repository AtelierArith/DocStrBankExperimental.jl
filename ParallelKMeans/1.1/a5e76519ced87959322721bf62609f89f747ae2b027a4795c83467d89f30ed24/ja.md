```
MiniBatch(b::Int)
`b`はサンプリングされるバッチのサイズを表します。

Sculley et al. 2007 ミニバッチk-meansアルゴリズムの実装。
```

```julia
X = rand(30, 100_000)  # 30次元の100_000個のランダムポイント

kmeans(MiniBatch(100), X, 3)  # 3つのクラスタ、各イテレーションで100バッチサンプルを使用したMiniBatchアルゴリズム
```
