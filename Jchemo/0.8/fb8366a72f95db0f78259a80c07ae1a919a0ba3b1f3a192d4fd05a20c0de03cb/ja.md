```
kplsrda(; kwargs...)
kplsrda(X, y; kwargs...)
kplsrda(X, y, weights::Weight; kwargs...)
```

カーネル部分最小二乗回帰に基づく識別 (KPLSR-DA)。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LV) の数。
  * `kern` : グラム行列を計算するために使用されるカーネルのタイプ。可能な値は: `:krbf`, `:kpol`。それぞれの関数 `krbf` と `kpol` のキーワード引数を参照してください。
  * `prior` : クラスメンバーシップのための事前確率のタイプ。可能な値は: `:prop` (比例)、`:unif` (一様)、または各クラスの事前重みを与えるベクトル (ベクトルの場合、`mlev(y)` と同じ順序でソートされている必要があります)。
  * `scal` : ブール値。`true` の場合、`X` と Yダミーの各列はその未修正の標準偏差でスケーリングされます。

関数 `plsrda` (PLSR-DA) と同様ですが、Yダミーテーブル上でPLSR (関数 `plskern`) の代わりにカーネルPLSR (関数 `kplsr`) が実行されます。

## 例

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/forages2.jld2")
@load db dat
@names dat
X = dat.X
Y = dat.Y
n = nro(X) 
s = Bool.(Y.test)
Xtrain = rmrow(X, s)
ytrain = rmrow(Y.typ, s)
Xtest = X[s, :]
ytest = Y.typ[s]
ntrain = nro(Xtrain)
ntest = nro(Xtest)
(ntot = n, ntrain, ntest)
tab(ytrain)
tab(ytest)

nlv = 15
kern = :krbf ; gamma = .001 
scal = true
model = kplsrda(; nlv, kern, gamma, scal) 
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
fitm.lev
fitm.ni

@head fitm.fitm.T
@head transf(model, Xtrain)
@head transf(model, Xtest)
@head transf(model, Xtest; nlv = 3)

coef(fitm.fitm)

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt

predict(model, Xtest; nlv = 1:2).pred
```
