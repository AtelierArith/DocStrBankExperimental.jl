```
predict(object::Union{Mbplsr, Mbplswest}, Xbl; nlv = nothing)
```

適合したモデルからY予測を計算します。

  * `object` : 適合したモデル。
  * `Xbl` : 予測が計算されるXデータのブロック（行列のベクトル）のリスト。
  * `nlv` : 考慮するLVの数、またはLVの数のコレクション。
