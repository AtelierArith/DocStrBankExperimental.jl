```
plswold(; kwargs...)
plswold(X, Y; kwargs...)
plswold(X, Y, weights::Weight; kwargs...)
plswold!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

部分最小二乗回帰 (PLSR) Woldアルゴリズムを使用

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。 `Weight` 型でなければなりません (例: 関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LV) の数。
  * `tol` : Nipalsアルゴリズムの許容誤差。
  * `maxit` : Nipalsアルゴリズムの最大反復回数。
  * `scal` : ブール値。 `true` の場合、`X` と `Y` の各列はその未修正標準偏差でスケーリングされます。

Wold Nipals PLSRアルゴリズム: Tenenhaus 1998 p.204。

例については関数 `plskern` を参照してください。

## 参考文献

Tenenhaus, M., 1998. La régression PLS: thÃ©orie et pratique.  Editions Technip, Paris, France.

Wold, S., Ruhe, A., Wold, H., Dunn, III, W.J., 1984. The  Collinearity Problem in Linear Regression. The Partial Least  Squares (PLS). Approach to Generalized Inverses. SIAM Journal on  Scientific and Statistical Computing 5, 735–743.  https://doi.org/10.1137/0905052
