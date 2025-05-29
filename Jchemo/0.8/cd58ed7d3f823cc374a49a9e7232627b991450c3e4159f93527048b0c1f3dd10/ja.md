```
knnda(; kwargs...)
knnda(X, y; kwargs...)
```

k-最近傍法重み付き判別 (kNN-DA)。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。

キーワード引数:

  * `metric` : 隣接点を選択し、重みを計算するために使用される非類似性のタイプ (関数 `getknn` を参照)。可能な値は: `:eucl` (ユークリッド)、`:mah` (マハラノビス)、`:sam` (スペクトル角距離)、`:cor` (相関距離)。
  * `h` : 関数 `winvs` によって計算される重み関数の形状を定義するスカラー。hが小さいほど、関数は鋭くなります。詳細については関数 `winvs` を参照してください（`winvs` のキーワード引数 `criw` と `squared` もここで指定できます）。
  * `k` : 各観測値を予測するために選択する最近傍の数。
  * `tolw` : 非常に近い隣接点の安定化のため。
  * `scal` : ブール値。`true` の場合、距離と重みの計算の前に、グローバル `X` の各列はその未修正の標準偏差でスケーリングされます。

この関数は関数 `knnr` と同じ原則を持っていますが、回帰の代わりに判別が行われます。近隣に対して重み付き投票が行われ、予測は最も頻繁なクラスに対応します。

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

metric = :eucl
h = 2 ; k = 10
model = knnda(; metric, h, k) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
fitm = model.fitm ;
fitm.lev
fitm.ni

res = predict(model, Xtest) ; 
@names res 
res.listnn
res.listd
res.listw
@head res.pred
@show errp(res.pred, ytest)
conf(res.pred, ytest).cnt

## 次元削減を使用して
model1 = pcasvd(; nlv = 15)
metric = :mah ; h = 1 ; k = 3 
model2 = knnda(; metric, h, k) 
model = pip(model1, model2)
fit!(model, Xtrain, ytrain)
@head pred = predict(model, Xtest).pred 
errp(pred, ytest)
```
