```
pcaeigenk(; kwargs...)
pcaeigenk(X; kwargs...)
pcaeigenk(X, weights::Weight; kwargs...)
pcaeigenk!(X::Matrix, weights::Weight; kwargs...)
```

カーネル行列 XX' の固有因子分解による PCA。

  * `X` : Xデータ (n, p)。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません (例: 関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 主成分 (PC) の数。
  * `scal` : ブール値。`true` の場合、`X` の各列はその未修正標準偏差でスケーリングされます。

これは PCA アルゴリズムの「カーネルクロスプロダクト」バージョンです (例: Wu et al. 1997)。広い行列 (n << p、ここで p は列の数) と n がそれほど大きくない場合、このアルゴリズムは他のものよりもはるかに高速です。

D を重みの (n, n) 対角行列 (`weights.w`) とし、X をメトリック D における中心化行列とします。この関数は、D^(1/2) * X * X' D^(1/2) の固有因子分解を計算することによって、メトリック D において ||X - T * V'||^2 を最小化します。

例については関数 `pcasvd` を参照してください。

## 参考文献

Wu, W., Massart, D.L., de Jong, S., 1997. 幅広いデータのためのカーネル PCA アルゴリズム。第 I 部: 理論とアルゴリズム。 Chemometrics and Intelligent Laboratory Systems 36, 165-172. https://doi.org/10.1016/S0169-7439(97)00010-5
