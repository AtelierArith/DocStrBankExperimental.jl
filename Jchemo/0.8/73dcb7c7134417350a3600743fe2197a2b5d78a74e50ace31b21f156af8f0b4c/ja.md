```
lda(; kwargs...)
lda(; kwargs...)
lda(X, y; kwargs...)
lda(X, y, weights::Weight; kwargs...)
```

線形判別分析 (LDA)。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数：

  * `prior` : クラスメンバーシップの事前確率のタイプ。可能な値は： `:prop` (比例)、 `:unif` (一様)、または各クラスの事前重みを与えるベクトル (ベクトルの場合、`mlev(y)` と同じ順序にソートされている必要があります)。

関数の低レベルメソッド (すなわち、引数 `weights` を持つ) は、中間計算で使用される任意の観測重みのベクトルを設定することを可能にします。高レベルメソッド (引数 `weights` がない) では、引数 `prior` の値から自動的に計算されます：各クラスについて、観測重みの合計はそのクラスに対応する事前確率と等しく設定されます。

**注意:** 非常に不均衡なクラスの場合、関数を使用する際に 'prior = :unif' を設定することが推奨される場合があります (パフォーマンスを評価する際には `errp` の代わりに `merrp` のようなスコアを使用すること)。

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

model = lda()
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
fitm.lev
fitm.ni
fitm.priors
aggsumv(fitm.weights.w, ytrain)

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt
```
