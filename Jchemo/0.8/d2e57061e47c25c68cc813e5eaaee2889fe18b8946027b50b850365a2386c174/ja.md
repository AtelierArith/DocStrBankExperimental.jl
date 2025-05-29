```
plsnipals(; kwargs...)
plsnipals(X, Y; kwargs...)
plsnipals(X, Y, weights::Weight; kwargs...)
plsnipals!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

ニパルスアルゴリズムを用いた部分最小二乗回帰（PLSR）。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません（例えば、関数 `mweight` を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数 (LV) の数。
  * `scal` : ブール値。`true` の場合、`X` と `Y` の各列はその未修正標準偏差でスケーリングされます。

この関数では、PLS2（多変量Y）のために、ニパルスの反復は行列 X'Y の SVD分解による PLS重み (w) の直接計算に置き換えられます（Hoskuldsson 1988 p.213）。

例については関数 `plskern` を参照してください。

## 参考文献

Hoskuldsson, A., 1988. PLS回帰法。化学計量学ジャーナル 2, 211-228.https://doi.org/10.1002/cem.1180020306

Tenenhaus, M., 1998. PLS回帰: 理論と実践。エディション・テクニップ、パリ、フランス。

Wold, S., Sjostrom, M., Eriksson, l., 2001. PLS回帰: 化学計量学の基本ツール。Chem. Int. Lab. Syst., 58, 109-130.
