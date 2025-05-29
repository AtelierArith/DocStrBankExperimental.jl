```
lwplsqda(; kwargs...)
lwplsqda(X, y; kwargs...)
```

kNN-LWPLS-QDA.

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。

キーワード引数:

  * `nlvdis` : 類似度を計算する前に次元削減に使用されるグローバルPLSで考慮する潜在変数 (LV) の数。`nlvdis = 0` の場合、次元削減は行われません。`nlvdis = 0` の場合、次元削減は行われません。
  * `metric` : 隣接点を選択し、重みを計算するために使用される類似度のタイプ (関数 `getknn` を参照)。可能な値は: `:eucl` (ユークリッド)、 `:mah` (マハラノビス)、 `:sam` (スペクトル角距離)、 `:cor` (相関距離)。
  * `h` : 関数 `winvs` によって計算される重み関数の形状を定義するスカラー。hが小さいほど、関数は鋭くなります。詳細については関数 `winvs` を参照してください (キーワード引数 `criw` と `squared` の `winvs` もここで指定できます)。
  * `k` : 各観測値を予測するために選択する最近傍の数。
  * `tolw` : 非常に近い隣接点の際の安定化のため。
  * `nlv` : ローカル (すなわち各近傍内) モデルの潜在変数 (LV) の数。
  * `prior` : クラスメンバーシップの事前確率のタイプ。可能な値は: `:unif` (一様)、 `:prop` (比例)。
  * `alpha` : QDA (`alpha = 0`) と LDA (`alpha = 1`) の間の連続体を定義するスカラー (∈ [0, 1])。
  * `scal` : ブール値。`true` の場合、(a) グローバル `X` の各列 (および事前のPLS次元削減がある場合のグローバル `Y`) は、距離と重みを計算する前に未修正の標準偏差でスケーリングされ、(b) XとYのスケーリングは、重み付きPLSRのために各近傍内 (ローカルレベル) でも行われます。
  * `verbose` : ブール値。`true` の場合、予測情報が印刷されます。

これは関数 `lwplsr` と同じ原則ですが、PLSRモデルの代わりにPLS-QDAモデルが各近傍にフィットされます。

  * **警告:** この関数の現在のバージョンは、近傍でQDAを行う際に非正定値行列による停止の影響を受ける可能性があります。これは、近傍内のいくつかのクラスが非常に少ない観測値を持つ可能性があるためです。十分に大きな数の隣接点を選択するか、または正則化されたQDA (`alpha > 0`) を使用することをお勧めします。

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

nlvdis = 25 ; metric = :mah
h = 2 ; k = 200
nlv = 10
model = lwplsqda(; nlvdis, metric, h, k, nlv, prior = :unif, alpha = .5) 
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
@show errp(res.pred, ytest)
conf(res.pred, ytest).cnt
```
