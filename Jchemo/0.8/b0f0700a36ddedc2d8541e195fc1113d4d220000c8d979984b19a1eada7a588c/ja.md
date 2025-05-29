```
plsravg(; kwargs...)
plsravg(X, Y; kwargs...)
plsravg(X, Y, weights::Weight; kwargs...)
plsravg!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

異なる潜在変数の数を持つPLSRモデルの平均化（PLSR-AVG）。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。    `Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数（LV）の数の範囲。
  * `scal` : ブール値。`true`の場合、`X`と`Y`の各列はその未修正の標準偏差でスケーリングされます。

異なる数のLVを持つモデルの予測を平均化することによって予測を計算するエンサンブリスト法。

例えば、引数`nlv`が`nlv` = `5:10`に設定されている場合、新しい観測の予測は、それぞれ5 LV、6 LV、... 10 LVのモデルによって返された予測の単純平均です。

## 参考文献

Lesnoff, M., Andueza, D., Barotin, C., Barre, V., Bonnal, L.,  Fernández Pierna, J.A., Picard, F., Vermeulen, V., Roger,  J.-M., 2022. Averaging and Stacking Partial Least Squares  Regression Models to Predict the Chemical Compositions and  the Nutritive Values of Forages from Spectral Near Infrared  Data. Applied Sciences 12, 7850.  https://doi.org/10.3390/app12157850

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/forages2.jld2") 
@load db dat
@names dat
X = dat.X 
Y = dat.Y
@head Y
y = Y.ndf
#y = Y.dm
n = nro(X)
s = Bool.(Y.test)
Xtrain = rmrow(X, s)
ytrain = rmrow(y, s)
Xtest = X[s, :]
ytest = y[s]
ntrain = nro(Xtrain)
ntest = nro(Xtest)
(ntot = n, ntrain, ntest)

nlv = 0:30
#nlv = 5:20
#nlv = 25
model = plsravg(; nlv) ;
fit!(model, Xtrain, ytrain)

res = predict(model, Xtest)
@head res.pred
res.predlv   # 各LVの数に対する予測 
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "予測",  
    ylabel = "観測値").f    
```
