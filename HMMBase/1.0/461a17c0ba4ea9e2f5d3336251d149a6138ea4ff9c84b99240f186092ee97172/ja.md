```
backward(a, A, LL) -> (Vector, Float)
```

サンプルの尤度を使用して後方確率を計算します。詳細は[前方-後方アルゴリズム](https://en.wikipedia.org/wiki/Forward–backward_algorithm)を参照してください。

**出力**

  * `Vector{Float64}`: 後方確率。
  * `Float64`: 観測された系列の対数尤度。
