```
mbplslda(; kwargs...)
mbplslda(Xbl, y; kwargs...)
mbplslda(Xbl, y, weights::Weight; kwargs...)
```

マルチブロック PLS-LDA。

  * `Xbl` : Xデータのブロックのリスト（行列のベクトル）    通常、（n, p）データの関数 `mblock` の出力。
  * `y` : 単変量クラスメンバーシップ（n）。
  * `weights` : 観測値の重み（n）。`Weight` 型でなければならない（例えば、関数 `mweight` を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数の数（LVs = スコア）。
  * `bscal` : ブロックスケーリングのタイプ。可能な値については関数 `blockscal` を参照。
  * `prior` : クラスメンバーシップのための事前確率のタイプ。可能な値は： `:prop`（比例）、 `:unif`（均一）、または各クラスの事前重みを与えるベクトル（ベクトルの場合、`mlev(y)` と同じ順序にソートされている必要がある）。
  * `scal` : ブール値。`true` の場合、`Xbl` の各ブロックの列と Ydummy は、MBPLS 計算においてブロックスケーリングの前にその未修正の標準偏差でスケーリングされる。

アプローチは次のとおりです：

1. 訓練変数 `y`（単変量クラスメンバーシップ）は、nlev 列を含むダミーテーブル（Ydummy）に変換されます。ここで nlev は `y` に存在するクラスの数です。Ydummy の各列はダミー（0/1）変数です。
2. {`X`, Ydummy} に対して多変量 MBPLSR（MBPLSR2）が実行され、スコア行列 `T` が返されます。
3. {`T`, `y`} に対して LDA が行われ、クラスメンバーシップの事後確率の推定値（∊ [0, 1]）が返されます。
4. 特定の観測に対して、最終的な予測は、確率推定が最も高いダミー変数に対応するクラスです。

関数の低レベルメソッド（すなわち、引数 `weights` を持つ）は、中間計算で使用される任意の観測重みのベクトルを設定することを可能にします。高レベルメソッド（引数 `weights` がない）では、クラスに対応する事前確率に等しくなるように、観測重みの合計が自動的に計算されます。

**注意:** 非常に不均衡なクラスの場合、関数を使用する際に 'prior = :unif' を設定することが推奨される場合があります（パフォーマンスを評価する際に `errp` の代わりに `merrp` のようなスコアを使用すること）。

## 例

```julia
using Jchemo, JLD2, CairoMakie, JchemoData
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/forages2.jld2")
@load db dat
@names dat
X = dat.X
Y = dat.Y
tab(Y.typ)
s = Bool.(Y.test)
Xtrain = rmrow(X, s)
ytrain = rmrow(Y.typ, s)
Xtest = X[s, :]
ytest = Y.typ[s]
ntrain = nro(Xtrain)
ntest = nro(Xtest)
ntot = ntrain + ntest
(ntot = ntot, ntrain, ntest)
wlst = names(X)
wl = parse.(Float64, wlst)
#plotsp(X, wl; nsamp = 20).f
##
listbl = [1:350, 351:700]
Xbltrain = mblock(Xtrain, listbl)
Xbltest = mblock(Xtest, listbl) 

nlv = 15
scal = false
#scal = true
bscal = :none
#bscal = :frob
model = mbplslda(; nlv, bscal, scal)
#model = mbplsqda(; nlv, bscal, alpha = .5, scal)
#model = mbplskdeda(; nlv, bscal, scal)
fit!(model, Xbltrain, ytrain) 
@names model 

@head transf(model, Xbltrain)
@head transf(model, Xbltest)

res = predict(model, Xbltest) ; 
@head res.pred 
@show errp(res.pred, ytest)
conf(res.pred, ytest).cnt

predict(model, Xbltest; nlv = 1:2).pred
```
