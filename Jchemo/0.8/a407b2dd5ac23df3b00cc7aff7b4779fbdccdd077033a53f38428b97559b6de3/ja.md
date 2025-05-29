```
splslda(; kwargs...)
splslda(X, y; kwargs...)
splslda(X, y, weights::Weight; kwargs...)
```

スパース PLS-LDA。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LV) の数。1以上でなければなりません。
  * `meth` : スパースしきい値処理に使用される方法。可能な値は `:soft`、`：hard` です。以下を参照してください。
  * `nvar` : 各 LV に選択される変数 (`X` 列) の数。単一の整数 (すなわち、各 LV に対して同じ数の変数) であるか、または長さ `nlv` のベクトルであることができます。
  * `prior` : クラスメンバーシップのための事前確率のタイプ。可能な値は `:prop` (比例)、`:unif` (一様)、または各クラスの事前重みを与えるベクトル (ベクトルの場合、`mlev(y)` と同じ順序でソートされている必要があります) です。
  * `scal` : ブール値。`true` の場合、PLS 計算において `X` と Ydummy の各列はその未修正の標準偏差でスケーリングされます。

関数 `plslda` (PLSR-LDA) と同様ですが、Yダミーテーブル上で PLSR (関数 `plskern` の代わりにスパース PLSR (関数 `splsr`) が実行されます。

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
model = splslda(; nlv, meth, nvar) 
#model = splsqda(; nlv, meth, nvar, alpha = .1) 
#model = splskdeda(; nlv, meth, nvar, a = .9) 
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
summary(embfitm, Xtrain)

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt

predict(model, Xtest; nlv = 1:2).pred
```
