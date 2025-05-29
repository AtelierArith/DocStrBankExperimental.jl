```
mlrpinv()
mlrpinv(X, Y; kwargs...)
mlrpinv(X, Y, weights::Weight; kwargs...)
mlrpinv!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

擬似逆行列を使用して多重線形回帰モデル (MLR) を計算します。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例: 関数 `mweight` を参照)。

キーワード引数:

  * `noint` : ブール値。モデルが切片ありで計算されるかどうかを定義します。

安全ですが、遅くなる可能性があります。

例については関数 `mlr` を参照してください。
