```
kpca(; kwargs...)
kpca(X; kwargs...)
kpca(X, weights::Weight; kwargs...)
```

カーネルPCA（Scholkopf et al. 1997, Scholkopf & Smola 2002, Tipping 2001）。

  * `X` : Xデータ (n, p)。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません（例えば、関数 `mweight` を参照）。

キーワード引数：

  * `nlv` : 考慮すべき主成分 (PC) の数。
  * `kern` : グラム行列を計算するために使用されるカーネルのタイプ。可能な値は `:krbf`, `:kpol` です。それぞれの関数 `krbf` と `kpol` のキーワード引数を参照してください。
  * `scal` : ブール値。`true` の場合、`X` の各列はその未修正の標準偏差でスケーリングされます。

このメソッドは、重み付きグラム行列のSVD因子分解によって実装されています：

  * D^(1/2) * Phi(X) * Phi(X)' * D^(1/2)

ここで、Xは中心化された行列で、Dは観測値（Xの行）の重み（`weights.w`）の対角行列です。

## 参考文献

Scholkopf, B., Smola, A., MÃ¼ller, K.-R., 1997. カーネル主成分分析, in: Gerstner, W., Germond, A., Hasler, M., Nicoud, J.-D. (Eds.), 人工ニューラルネットワーク, ICANN 97, コンピュータサイエンスの講義ノート. Springer, Berlin, Heidelberg, pp. 583-588. https://doi.org/10.1007/BFb0020217

Scholkopf, B., Smola, A.J., 2002. カーネルを用いた学習: サポートベクターマシン, 正則化, 最適化, そしてそれ以降, 適応計算と機械学習. MIT Press, Cambridge, Mass.

Tipping, M.E., 2001. スパースカーネル主成分分析. 神経情報処理システムの進展, MIT Press. http://papers.nips.cc/paper/1791-sparse-kernel-principal-component-analysis.pdf

## 例

```julia
using Jchemo, JchemoData, JLD2 
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2") 
@load db dat
@names dat
@head dat.X
X = dat.X[:, 1:4]
n = nro(X)
ntest = 30
s = samprand(n, ntest) 
Xtrain = X[s.train, :]
Xtest = X[s.test, :]

nlv = 3
kern = :krbf ; gamma = 1e-4
model = kpca(; nlv, kern, gamma) ;
fit!(model, Xtrain)
@names model.fitm
@head T = model.fitm.T
T' * T
model.fitm.V' * model.fitm.V

@head Ttest = transf(model, Xtest)

res = summary(model) ;
@names res
res.explvarx
```
