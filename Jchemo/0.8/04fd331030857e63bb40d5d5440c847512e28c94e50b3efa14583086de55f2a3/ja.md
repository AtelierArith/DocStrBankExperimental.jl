```
krrda(; kwargs...)
krrda(X, y; kwargs...)
krrda(X, y, weights::Weight; kwargs...)
```

カーネルリッジ回帰に基づく識別 (KRR-DA)。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `lb` : リッジ正則化パラメータ "lambda"。
  * `kern` : グラム行列を計算するために使用されるカーネルのタイプ。可能な値は: `:krbf`, `:kpol`。それぞれの関数 `krbf` と `kpol` のキーワード引数を参照してください。
  * `prior` : クラスメンバーシップのための事前確率のタイプ。可能な値は: `:prop` (比例)、`:unif` (一様)、または各クラスの事前重みを与えるベクトル (ベクトルの場合、`mlev(y)` と同じ順序でソートされている必要があります)。
  * `scal` : ブール値。`true` の場合、`X` の各列はその未修正の標準偏差でスケーリングされます。

関数 `rrda` (RR-DA) と同様ですが、Yダミーテーブル上でRR (関数 `rr`) の代わりにカーネルRR (関数 `krr`) が実行されます。

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

lb = 1e-5
kern = :krbf ; gamma = .001 
scal = true
model = krrda(; lb, kern, gamma, scal) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
fitm = model.fitm ;
fitm.lev
fitm.ni

coef(fitm.fitm)

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt

predict(model, Xtest; lb = [.1, .001]).pred
```
