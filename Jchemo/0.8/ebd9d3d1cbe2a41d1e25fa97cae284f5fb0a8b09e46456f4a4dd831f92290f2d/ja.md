```
lwmlr(; kwargs...)
lwmlr(X, Y; kwargs...)
```

k-最近傍法による局所加重重回帰分析 (kNN-LWMLR)。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。

キーワード引数:

  * `metric` : 隣接点を選択し、重みを計算するために使用される非類似性のタイプ (関数 `getknn` を参照)。可能な値は: `:eucl` (ユークリッド)、`:mah` (マハラノビス)、`:sam` (スペクトル角距離)、`:cor` (相関距離)。
  * `h` : 関数 `winvs` によって計算される重み関数の形状を定義するスカラー。hが小さいほど、関数は鋭くなります。詳細については関数 `winvs` を参照してください（`winvs` のキーワード引数 `criw` と `squared` もここで指定できます）。
  * `k` : 各観測値を予測するために選択する最近傍の数。
  * `tolw` : 非常に近い隣接点の際の安定化のため。
  * `scal` : ブール値。`true` の場合、距離と重みの計算の前に、グローバル `X` の各列はその未修正の標準偏差でスケーリングされます。
  * `verbose` : ブール値。`true` の場合、予測情報が印刷されます。

これは関数 `lwplsr` と同じ原理ですが、MLRモデルはPLSRモデルの代わりに近傍にフィットされます。近傍は `X` に直接計算されます（事前の次元削減はありません）。

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

nlv = 20
model0 = pcasvd(; nlv) ;
fit!(model0, Xtrain) 
@head Ttrain = model0.fitm.T 
@head Ttest = transf(model0, Xtest)

metric = :eucl 
h = 2 ; k = 100 
model = lwmlr(; metric, h, k) 
fit!(model, Ttrain, ytrain)
@names model
@names model.fitm
dump(model.fitm.par)

res = predict(model, Ttest) ; 
@names res 
res.listnn
res.listd
res.listw
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "予測",  
    ylabel = "観測値").f    

####### 関数 sinc(x) のフィッティングの例
####### Rosipal & Trejo 2001 p. 105-106 に記載されている 
x = collect(-10:.2:10) 
x[x .== 0] .= 1e-5
n = length(x)
zy = sin.(abs.(x)) ./ abs.(x) 
y = zy + .2 * randn(n) 
model = lwmlr(metric = :eucl, h = 1.5, k = 20) ;
fit!(model, x, y)
pred = predict(model, x).pred 
f, ax = scatter(x, y) 
lines!(ax, x, zy, label = "真のモデル")
lines!(ax, x, vec(pred), label = "フィッティングモデル")
axislegend("方法")
f
```
