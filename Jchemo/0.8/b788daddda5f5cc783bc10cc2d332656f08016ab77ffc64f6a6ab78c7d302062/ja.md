```
predict(object::Kplsr, X; nlv = nothing)
```

フィットしたモデルからY予測を計算します。

  * `object` : フィットしたモデル。
  * `X` : 予測が計算されるXデータ。
  * `nlv` : 考慮するLVの数、またはLVの数のコレクション。

何も指定しない場合、最大LVの数になります。
