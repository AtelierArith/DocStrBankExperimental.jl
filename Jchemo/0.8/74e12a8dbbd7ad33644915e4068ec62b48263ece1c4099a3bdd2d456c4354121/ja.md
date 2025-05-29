```
plskdeda(; kwargs...)
plskdeda(X, y; kwargs...)
plskdeda(X, y, weights::Weight; kwargs...)
```

PLS潜在変数におけるKDE-DA（PLS-KDEDA）。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数 (LV) の数。1以上でなければなりません。
  * `prior` : クラスメンバーシップの事前確率のタイプ。可能な値は、`:prop`（比例）、`:unif`（一様）、または各クラスの事前重みを与えるベクトル（ベクトルの場合、`mlev(y)`と同じ順序でソートされている必要があります）。
  * `scal` : ブール値。`true`の場合、PLS計算において`X`とYdummyの各列はその未修正標準偏差でスケーリングされます。
  * 関数`dmkern`のキーワード引数（バンド幅定義）もここで指定できます。

関数`plsqda`と同様ですが、クラス密度は`dmnorm`の代わりに`dmkern`から推定されます。

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
model = plskdeda(; nlv) 
#model = plskdeda(; nlv, prior = :unif) 
#model = plskdeda(; nlv, a = .5)
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
fitm.lev
fitm.ni

embfitm = fitm.fitm.embfitm ;
@head embfitm.T
@head transf(model, Xtrain)
@head transf(model, Xtest)
@head transf(model, Xtest; nlv = 3)

coef(embfitm)

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt

predict(model, Xtest; nlv = 1:2).pred
summary(embfitm, Xtrain)
```
