```
plssimp(; kwargs...)
plssimp(X, Y; kwargs...)
plssimp(X, Y, weights::Weight; kwargs...)
plssimp!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

部分最小二乗回帰 (PLSR) を SIMPLS アルゴリズム (de Jong 1993) を用いて行います。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。 `Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LV) の数。
  * `scal` : ブール値。 `true` の場合、`X` と `Y` の各列はその未修正の標準偏差でスケーリングされます。

**注意:** この関数では、スコア T (LV) は正規化されておらず、de Jong (2013) の元のアルゴリズムとは逆です。

例については関数 `plskern` を参照してください。

## 参考文献

de Jong, S., 1993. SIMPLS: An alternative approach to  partial least squares regression. Chemometrics and Intelligent  Laboratory Systems 18, 251–263.  https://doi.org/10.1016/0169-7439(93)85002-X
