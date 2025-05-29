```
lwmlrda(; kwargs...)
lwmlrda(X, y; kwargs...)
```

k-最近傍法に基づく局所加重MLRによる識別 (kNN-LWMLR-DA)。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。

キーワード引数:

  * `metric` : 隣接点を選択し、重みを計算するために使用される非類似性のタイプ (関数 `getknn` を参照)。可能な値は: `:eucl` (ユークリッド)、`:mah` (マハラノビス)、`:sam` (スペクトル角距離)、`:cor` (相関距離)。
  * `h` : 関数 `winvs` によって計算される重み関数の形状を定義するスカラー。hが小さいほど、関数は鋭くなります。詳細については関数 `winvs` を参照してください（`winvs` のキーワード引数 `criw` と `squared` もここで指定できます）。
  * `k` : 各観測値を予測するために選択する最近傍の数。
  * `tolw` : 非常に近い隣接点の際の安定化のため。
  * `scal` : ブール値。`true` の場合、距離と重みの計算の前に、グローバル `X` の各列はその未修正の標準偏差でスケーリングされます。
  * `verbose` : ブール値。`true` の場合、予測情報が印刷されます。

これは関数 `lwmlr` と同じ原理ですが、MLRモデルの代わりにMLR-DAモデルが近隣にフィットされます。

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

metric = :mah
h = 2 ; k = 10
model = lwmlrda(; metric, h, k) 
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
fitm.lev
fitm.ni

res = predict(model, Xtest) ; 
@names res 
res.listnn
res.listd
res.listw
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt
```
