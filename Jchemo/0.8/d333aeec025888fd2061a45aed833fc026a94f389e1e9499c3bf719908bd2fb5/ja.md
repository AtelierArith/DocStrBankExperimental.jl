```
qda(; kwargs...)
qda(X, y; kwargs...)
qda(X, y, weights::Weight; kwargs...)
```

二次判別分析 (QDA、LDAへの連続体を含む)。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `prior` : クラスメンバーシップの事前確率のタイプ。可能な値は: `:prop` (比例)、`：unif` (一様)、または各クラスの事前重みを与えるベクトル (ベクトルの場合、`mlev(y)` と同じ順序にソートされている必要があります)。
  * `alpha` : QDA (`alpha = 0`) と LDA (`alpha = 1`) の間の連続体を定義するスカラー (∈ [0, 1])。

関数の低レベルメソッド (すなわち、引数 `weights` を持つ) は、中間計算で使用される任意の観測重みのベクトルを設定することを可能にします。高レベルメソッド (引数 `weights` がない) では、引数 `prior` の値から自動的に計算されます: 各クラスについて、観測重みの合計はそのクラスに対応する事前確率と等しく設定されます。

**注意:** 非常に不均衡なクラスの場合、関数を使用する際に 'prior = :unif' を設定することが推奨される場合があります (パフォーマンスを評価する際に `errp` の代わりに `merrp` のようなスコアを使用すること)。

連続体アプローチでは、値 `alpha` > 0 はクラス共分散 (Wi) を共通の LDA 共分散 ('within-W') に向かって縮小します。これは、Friedman 1989 で説明されている '最初の正則化 (Eqs.16)' アプローチに対応します (この場合のパラメータ `alpha` は 'lambda' と呼ばれます)。

## 参考文献

Friedman JH. Regularized Discriminant Analysis. Journal of the American Statistical Association. 1989;  84(405):165-175. doi:10.1080/01621459.1989.10478752.

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

model = qda()
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

## 正則化あり
model = qda(alpha = .5)
#model = qda(alpha = 1) # = LDA
fit!(model, Xtrain, ytrain)
model.fitm.Wi
res = predict(model, Xtest) ;
errp(res.pred, ytest)
```
