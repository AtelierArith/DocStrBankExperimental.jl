```
mlrvec(; kwargs...)
mlrvec(X, Y; kwargs...)
mlrvec(X, Y, weights::Weight; kwargs...)
mlrvec!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

単純な（単変量 x）線形回帰モデルを計算します。

  * `x` : 単変量 X データ (n)。
  * `Y` : Y データ (n, q)。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません（例えば、関数 `mweight` を参照）。

キーワード引数：

  * `noint` : ブール値。モデルが切片ありで計算されるかどうかを定義します。

例については関数 `mlr` を参照してください。
