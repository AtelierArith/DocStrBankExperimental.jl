```
kdeda(; kwargs...)
kdeda(X, y; kwargs...)
```

非パラメトリックカーネルガウス密度推定（KDE-DA）を使用した判別分析。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。

キーワード引数:

  * `prior` : クラスメンバーシップの事前確率のタイプ。可能な値は、`:prop`（比例）、`:unif`（一様）、または各クラスの事前重みを与えるベクトル（ベクトルの場合、`mlev(y)`と同じ順序でソートされている必要があります）。
  * 関数`dmkern`のキーワード引数（バンド幅定義）もここで指定できます。

関数`qda`と同様ですが、クラス密度は関数`dmnorm`の代わりに関数`dmkern`から推定されます。

## 例

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2")
@load db dat
@names dat
@head dat.X
X = dat.X[:, 1:4]
y = dat.X[:, 5]
n = nro(X)
ntest = 30
s = samprand(n, ntest)
Xtrain = X[s.train, :]
ytrain = y[s.train]
Xtest = X[s.test, :]
ytest = y[s.test]
ntrain = n - ntest
(ntot = n, ntrain, ntest)
tab(ytrain)
tab(ytest)

prior = :unif
#prior = :prop
model = kdeda(; prior)
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
fitm.lev
fitm.ni

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt

model = kdeda(; prior, a = .5) 
#model = kdeda(; prior, h = .1) 
fit!(model, Xtrain, ytrain)
model.fitm.fitm[1].H
```
