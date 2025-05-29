```
mlrda(; kwargs...)
mlrda(X, y; kwargs...)
mlrda(X, y, weights::Weight)
```

多重線形回帰に基づく識別（MLR-DA）。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません（例えば、関数 `mweight` を参照）。

キーワード引数：

  * `prior` : クラスメンバーシップの事前確率のタイプ。可能な値は、`:prop`（比例）、`:unif`（一様）、または各クラスの事前重みを与えるベクトル（ベクトルの場合、`mlev(y)` と同じ順序にソートされている必要があります）。

アプローチは次のとおりです：

1. トレーニング変数 `y`（単変量クラスメンバーシップ）は、nlev列を含むダミーテーブル（Ydummy）に変換されます。ここで、nlevは `y` に存在するクラスの数です。Ydummyの各列はダミー（0/1）変数です。
2. 次に、{`X`, Ydummy} に対して多重線形回帰（MLR）が実行され、ダミー変数の予測（= 関数 `predict` によって返されるオブジェクト `posterior`）が返されます。これらの予測は、クラスメンバーシップ確率の無制限の推定値（すなわち、最終的に [0, 1] の外にある可能性がある）と見なすことができます。
3. 特定の観測値に対して、最終的な予測は、確率推定が最も高いダミー変数に対応するクラスです。

関数の低レベルメソッド（すなわち、引数 `weights` を持つ）は、中間計算に使用される任意の観測重みのベクトルを設定することを可能にします。高レベルメソッド（引数 `weights` がない）では、クラスごとに観測重みの合計がそのクラスに対応する事前確率に等しく設定されます。

**注意:** 非常に不均衡なクラスの場合、関数を使用する際に 'prior = :unif' を設定することが推奨される場合があります（パフォーマンスを評価する際に `errp` の代わりに `merrp` のようなスコアを使用すること）。

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

model = mlrda()
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
```
