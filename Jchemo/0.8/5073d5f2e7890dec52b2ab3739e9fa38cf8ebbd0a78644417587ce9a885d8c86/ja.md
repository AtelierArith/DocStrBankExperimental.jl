```
gridscore(model::Pipeline, Xtrain, Ytrain, X, Y; score, pars = nothing, 
    nlv = nothing, lb = nothing, verbose = false)
```

モデルパイプラインのパラメータグリッドに対するテストセット検証。

  * `model` : 評価するモデルのパイプライン。
  * `Xtrain` : トレーニングXデータ (n, p)。
  * `Ytrain` : トレーニングYデータ (n, q)。
  * `X` : 検証Xデータ (m, p)。
  * `Y` : 検証Yデータ (m, q)。

キーワード引数: 

  * `score` : 予測スコアを計算する関数 (例: `rmsep`)。
  * `pars` : 同じ長さの名前付きベクトルのタプルで、パラメータの組み合わせを定義する (例: 関数 `mpar` の出力)。
  * `verbose` : `true` の場合、予測情報が出力される。
  * `nlv` : 潜在変数 (LV) の数の値または値のベクトル。
  * `lb` : リッジ正則化パラメータ "lambda" の値または値のベクトル。

この関数の現在のバージョンでは、パイプラインの最後のモデル (= 最終予測器) のみが検証される。

その他の詳細については、単純モデルのための関数 `gridscore` を参照してください。

## 例

```julia
using JLD2, CairoMakie, JchemoData
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "cassav.jld2") 
@load db dat
@names dat
X = dat.X 
y = dat.Y.tbc
year = dat.Y.year
tab(year)
s = year .<= 2012
Xtrain = X[s, :]
ytrain = y[s]
Xtest = rmrow(X, s)
ytest = rmrow(y, s)
ntrain = nro(Xtrain)
ntest = nro(Xtest)
ntot = ntrain + ntest
(ntot = ntot, ntrain, ntest)
## CalとValの構築 
## トレーニング内
nval = round(Int, .3 * ntrain)
s = samprand(ntrain, nval)
Xcal = Xtrain[s.train, :]
ycal = ytrain[s.train]
Xval = Xtrain[s.test, :]
yval = ytrain[s.test]

####-- パイプライン Snv :> Savgol :> Plsr
## 最後のモデルのみが検証される
## model1
model1 = snv()
## model2 
npoint = 11 ; deriv = 2 ; degree = 3
model2 = savgol(; npoint, deriv, degree)
## model3
nlv = 0:30
model3 = plskern()
##
model = pip(model1, model2, model3)
res = gridscore(model, Xcal, ycal, Xval, yval; score = rmsep, nlv) ;
plotgrid(res.nlv, res.y1; step = 2, xlabel = "Nb. LVs", ylabel = "RMSEP").f
u = findall(res.y1 .== minimum(res.y1))[1] 
res[u, :]
model3 = plskern(nlv = res.nlv[u])
model = pip(model1, model2, model3)
fit!(model, Xtrain, ytrain)
res = predict(model, Xtest) ; 
@head res.pred 
rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction",
      ylabel = "Observed").f

####-- パイプライン Pca :> Svmr
## 最後のモデルのみが検証される
## model1
nlv = 15 ; scal = true
model1 = pcasvd(; nlv, scal)
## model2
kern = [:krbf]
gamma = (10).^(-5:1.:5)
cost = (10).^(1:3)
epsilon = [.1, .2, .5]
pars = mpar(kern = kern, gamma = gamma, cost = cost, epsilon = epsilon)
model2 = svmr()
##
model = pip(model1, model2)
res = gridscore(model, Xcal, ycal, Xval, yval; score = rmsep, pars, verbose = true)
u = findall(res.y1 .== minimum(res.y1))[1] 
res[u, :]
model2 = svmr(kern = res.kern[u], gamma = res.gamma[u], cost = res.cost[u], epsilon = res.epsilon[u])
model = pip(model1, model2) 
fit!(model, Xtrain, ytrain)
res = predict(model, Xtest) ; 
@head res.pred 
rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction",
      ylabel = "Observed").f
```
