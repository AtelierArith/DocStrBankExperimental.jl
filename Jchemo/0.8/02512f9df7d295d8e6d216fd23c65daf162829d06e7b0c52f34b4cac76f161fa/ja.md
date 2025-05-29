```
splsrda(; kwargs...)
splsrda(X, y; kwargs...)
splsrda(X, y, weights::Weight; kwargs...)
```

スパースPLSR-DA。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数: 

  * `nlv` : 計算する潜在変数 (LV) の数。
  * `meth` : スパースしきい値処理に使用される方法。可能な値は `:soft`, `:hard` です。以下を参照してください。
  * `nvar` : 各LVに選択される変数 (`X`-列) の数。単一の整数（すなわち、各LVに対して同じ数の変数）または長さ `nlv` のベクトルであることができます。
  * `prior` : クラスメンバーシップの事前確率のタイプ。可能な値は `:prop`（比例）、`:unif`（一様）、または各クラスの事前重みを与えるベクトル（ベクトルの場合、`mlev(y)`と同じ順序でソートされている必要があります）です。
  * `scal` : ブール値。`true`の場合、`X`およびYダミーの各列は、その未修正の標準偏差でスケーリングされます。

関数`plsrda`（PLSR-DA）と同様ですが、PLSR（関数`splsr`）ではなく、スパースPLSRがYダミーテーブルで実行されます。

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
meth = :soft
nvar = 10
model = splsrda(; nlv, meth, nvar) 
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
summary(fitm.fitm, Xtrain)
```
