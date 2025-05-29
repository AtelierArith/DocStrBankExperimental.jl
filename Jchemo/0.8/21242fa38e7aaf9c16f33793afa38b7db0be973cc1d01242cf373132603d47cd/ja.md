```
plslda(; kwargs...)
plslda(X, y; kwargs...)
plslda(X, y, weights::Weight; kwargs...)
```

PLS潜在変数上でのLDA（PLS-LDA）。

  * `X` : Xデータ (n, p)。
  * `y` : 一変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数 (LV) の数。1以上でなければなりません。
  * `prior` : クラスメンバーシップの事前確率のタイプ。可能な値は、`:prop`（比例）、`:unif`（均一）、または各クラスの事前重みを与えるベクトル（ベクトルの場合、`mlev(y)`と同じ順序にソートされている必要があります）。
  * `scal` : ブール値。`true`の場合、PLS計算において、`X`とYdummyの各列はその未修正標準偏差でスケーリングされます。

PLS潜在変数上でのLDA。アプローチは次のとおりです：

1. 訓練変数`y`（一変量クラスメンバーシップ）は、nlev列を含むダミーテーブル（Ydummy）に変換されます。ここで、nlevは`y`に存在するクラスの数です。Ydummyの各列はダミー（0/1）変数です。
2. {`X`, Ydummy}に対して多変量PLSR（PLSR2）が実行され、スコア行列`T`が返されます。
3. {`T`, `y`}に対してLDAが行われ、クラスメンバーシップの事後確率の推定値（∊ [0, 1]）が返されます。
4. 特定の観測値に対して、最終的な予測は、確率推定が最も高いダミー変数に対応するクラスです。

関数の低レベルメソッド（すなわち、引数`weights`を持つ）は、中間計算で使用される観測値の重みの任意のベクトルを設定することを可能にします。高レベルメソッド（引数`weights`なし）では、引数`prior`の値から自動的に計算されます：各クラスについて、観測値の重みの合計は、そのクラスに対応する事前確率と等しく設定されます。

**注意:** 非常に不均衡なクラスの場合、関数を使用する際に'prior = :unif'を設定することが推奨される場合があります（パフォーマンスを評価する際に`errp`の代わりに`merrp`のようなスコアを使用すること）。

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
model = plslda(; nlv) 
#model = plslda(; nlv, prior = :unif) 
#model = plsqda(; nlv, alpha = .1) 
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
