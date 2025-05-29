```
plsrosa(; kwargs...)
plsrosa(X, Y; kwargs...)
plsrosa(X, Y, weights::Weight; kwargs...)
plsrosa!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

部分最小二乗回帰 (PLSR) と ROSA アルゴリズム (Liland et al. 2016)。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。    `Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LV) の数。
  * `scal` : ブール値。`true` の場合、`X` と `Y` の各列はその未修正標準偏差でスケーリングされます。

**注意:** この関数は Liland et al. (2016) の元のアルゴリズムと以下の点で異なります:

  * スコア T (LV) は正規化されていません。
  * 多変量 Y が許可されています。

例については関数 `plskern` を参照してください。

## 参考文献

Liland, K.H., Næs, T., Indahl, U.G., 2016. ROSA—多ブロックデータ分析のための部分最小二乗回帰の高速拡張。化学計量学ジャーナル 30, 651–662.  https://doi.org/10.1002/cem.2824
