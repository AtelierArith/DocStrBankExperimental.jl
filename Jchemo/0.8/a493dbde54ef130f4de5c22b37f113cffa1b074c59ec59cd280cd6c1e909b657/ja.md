```
plsrda(; kwargs...)
plsrda(X, y; kwargs...)
plsrda(X, y, weights::Weight; kwargs...)
```

部分最小二乗回帰に基づく識別（PLSR-DA）。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません（例えば、関数 `mweight` を参照）。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LV) の数。
  * `prior` : クラスメンバーシップの事前確率のタイプ。可能な値は、`:prop`（比例）、`:unif`（一様）、または各クラスの事前重みを与えるベクトル（ベクトルの場合、`mlev(y)` と同じ順序にソートされている必要があります）。
  * `scal` : ブール値。`true` の場合、`X` と Ydummy の各列はその未修正標準偏差でスケーリングされます。

これは通常の「PLSDA」です。アプローチは次のとおりです：

1. 訓練変数 `y`（単変量クラスメンバーシップ）は、nlev 列を含むダミーテーブル (Ydummy) に変換されます。ここで nlev は `y` に存在するクラスの数です。Ydummy の各列はダミー（0/1）変数です。
2. 次に、{`X`, Ydummy} に対して多変量 PLSR (PLSR2) が実行され、ダミー変数の予測 (= 関数 `predict` によって返されるオブジェクト `posterior`) が返されます。これらの予測は、クラスメンバーシップ確率の無制限の推定値（すなわち、最終的には [0, 1] の外にある可能性がある）と見なすことができます。
3. 特定の観測に対して、最終的な予測は、確率推定が最も高いダミー変数に対応するクラスです。

関数の低レベルメソッド（すなわち、引数 `weights` を持つ）は、中間計算に使用される任意の観測重みのベクトルを設定することを可能にします。高レベルメソッド（引数 `weights` がない）では、これらは引数 `prior` の値から自動的に計算されます：各クラスについて、観測重みの合計は、そのクラスに対応する事前確率と等しく設定されます。

**注意:** 非常に不均衡なクラスの場合、関数を使用する際に 'prior = :unif' を設定することが推奨される場合があります（パフォーマンスを評価する際に `errp` の代わりに `merrp` のようなスコアを使用すること）。

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
model = plsrda(; nlv) 
#model = plsrda(; nlv, prior = :unif) 
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
fitm.lev
fitm.ni
@names fitm.fitm
aggsumv(fitm.fitm.weights.w, ytrain)

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
