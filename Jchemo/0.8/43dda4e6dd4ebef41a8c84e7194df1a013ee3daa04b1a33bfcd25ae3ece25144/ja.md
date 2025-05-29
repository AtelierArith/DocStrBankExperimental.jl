```
mlrchol()
mlrchol(X, Y)
mlrchol(X, Y, weights::Weight)
mlrchol!mlrchol!(X::Matrix, Y::Matrix, weights::Weight)
```

正規方程式とコレスキー分解を使用して、重回帰モデル（MLR）を計算します。

  * `X` : Xデータ、列数が2以上である必要があります（関数choleskyによって要求されます）。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。`Weight`型でなければなりません（例えば、関数`mweight`を参照）。

切片を持つモデルのみを計算します。

より速いですが、精度が低くなる可能性があります（平方要素X'Xに基づく）。

例については関数`mlr`を参照してください。
