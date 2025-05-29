```
knnr(; kwargs...)
knnr(X, Y; kwargs...)
```

k-最近傍法加重回帰 (KNNR)。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。

キーワード引数：

  * `metric` : 隣接点を選択し、重みを計算するために使用される非類似性のタイプ (関数 `getknn` を参照)。可能な値は： `:eucl` (ユークリッド)、 `:mah` (マハラノビス)、 `:sam` (スペクトル角距離)、 `:cor` (相関距離)。
  * `h` : 関数 `winvs` によって計算される重み関数の形状を定義するスカラー。hが小さいほど、関数は鋭くなります。詳細については関数 `winvs` を参照してください（`winvs` のキーワード引数 `criw` と `squared` もここで指定できます）。
  * `k` : 各観測値を予測するために選択する最近傍の数。
  * `tolw` : 非常に近い隣接点の安定化のため。
  * `scal` : ブール値。 `true` の場合、距離と重みの計算の前に、グローバル `X` の各列はその未修正の標準偏差でスケーリングされます。

この関数の一般的な原則は次のとおりです（kNNRパイプラインの他の多くのバリエーションを構築できます）： a) 予測する新しい観測値ごとに、予測は選択された近隣（`X`内）のサイズ `k` にわたる `y` の加重平均です。 b) 選択された近隣内では、重みは新しい観測値と近隣との非類似性から定義され、関数 'winvs' から計算されます。

一般に、高次元のXデータの場合、マハラノビス距離を使用するには、事前の次元削減が必要です（例を参照）。

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
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

h = 1 ; k = 3 
model = knnr(; h, k) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
dump(model.fitm.par)
res = predict(model, Xtest) ; 
@names res 
res.listnn
res.listd
res.listw
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "予測", 
    ylabel = "観測").f    

## 次元削減を使用して
model1 = pcasvd(nlv = 15)
metric = :eucl ; h = 1 ; k = 3 
model2 = knnr(; metric, h, k) 
model = pip(model1, model2)
fit!(model, Xtrain, ytrain)
res = predict(model, Xtest) ; 
@head res.pred
@show rmsep(res.pred, ytest)

####### 関数 sinc(x) のフィッティングの例
####### Rosipal & Trejo 2001 p. 105-106 に記載
x = collect(-10:.2:10) 
x[x .== 0] .= 1e-5
n = length(x)
zy = sin.(abs.(x)) ./ abs.(x) 
y = zy + .2 * randn(n) 
model = knnr(k = 15, h = 5) 
fit!(model, x, y)
pred = predict(model, x).pred 
f, ax = scatter(x, y) 
lines!(ax, x, zy, label = "真のモデル")
lines!(ax, x, vec(pred), label = "フィッティングモデル")
axislegend("方法")
f
```
