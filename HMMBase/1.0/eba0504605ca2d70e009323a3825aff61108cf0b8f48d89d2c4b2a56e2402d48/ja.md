```
forward(a, A, LL) -> (Vector, Float)
```

サンプルの尤度を使用して前向き確率を計算します。詳細は[フォワード・バックワードアルゴリズム](https://en.wikipedia.org/wiki/Forward–backward_algorithm)を参照してください。

**出力**

  * `Vector{Float64}`: 前向き確率。
  * `Float64`: 観測された列の対数尤度。
