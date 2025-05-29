```
mlrpinvn() 
mlrpinvn(X, Y)
mlrpinvn(X, Y, weights::Weight)
mlrpinvn!mlrchol!(X::Matrix, Y::Matrix, 
    weights::Weight)
```

正規方程式と擬似逆行列を使用して、重回帰モデル（MLR）を計算します。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません（例えば、関数 `mweight` を参照）。

pがそれほど大きくない場合、安全で高速です。

切片を持つモデルのみを計算します。

例については関数 `mlr` を参照してください。
