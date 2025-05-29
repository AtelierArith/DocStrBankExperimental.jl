```
lwplsravg(; kwargs...)
lwplsravg(X, Y; kwargs...)
```

異なる数の潜在変数を持つkNN-LWPLSRモデルの平均化（kNN-LWPLSR-AVG）。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。

キーワード引数：

  * `nlvdis` : 次元削減のために使用されるグローバルPLSで考慮する潜在変数（LV）の数。`nlvdis = 0`の場合、次元削減は行われません。`nlvdis = 0`の場合、次元削減は行われません。
  * `metric` : 隣接点を選択し、重みを計算するために使用される類似度のタイプ（関数`getknn`を参照）。可能な値は：`:eucl`（ユークリッド）、`:mah`（マハラノビス）、`:sam`（スペクトル角距離）、`:cor`（相関距離）。
  * `h` : 関数`winvs`によって計算される重み関数の形状を定義するスカラー。hが小さいほど、関数は鋭くなります。詳細については関数`winvs`を参照してください（`winvs`のキーワード引数`criw`と`squared`もここで指定できます）。
  * `k` : 各観測値を予測するために選択する最近傍の数。
  * `tolw` : 非常に近い隣接点の安定化のため。
  * `nlv` : ローカル（すなわち各近傍内）モデルのために計算する潜在変数（LV）の数の範囲。
  * `scal` : ブール値。`true`の場合、(a) グローバル`X`の各列（および事前のPLS次元削減がある場合のグローバル`Y`）は、距離と重みを計算する前にその未修正の標準偏差でスケーリングされ、(b) XとYのスケーリングも各近傍内（ローカルレベル）で重み付きPLSRのために行われます。
  * `verbose` : ブール値。`true`の場合、予測情報が印刷されます。

異なる数のLVを持つモデルの予測を平均化することによって予測を計算するエンセムブリスト法。Lesnoff 2023のように。各近傍で、PLSRの代わりにPLSR平均化（Lesnoff et al. 2022）が行われます。

例えば、引数`nlv`が`nlv` = `5:10`に設定されている場合、新しい観測値の予測は、5 LV、6 LV、... 10 LVのモデルによって返される予測の単純平均です。

## 参考文献

Lesnoff, M., Andueza, D., Barotin, C., Barre, V., Bonnal, L., Fernández Pierna, J.A., Picard, F.,  Vermeulen, V., Roger, J.-M., 2022. Averaging and Stacking Partial Least Squares  Regression Models to Predict the Chemical Compositions and the Nutritive Values of Forages from  Spectral Near Infrared Data. Applied Sciences 12, 7850. https://doi.org/10.3390/app12157850

M. Lesnoff, Averaging a local PLSR pipeline to predict chemical compositions and nutritive values of forages  and feed from spectral near infrared data, Chemometrics and Intelligent Laboratory Systems. 244 (2023) 105031.  https://doi.org/10.1016/j.chemolab.2023.105031.

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

nlvdis = 5 ; metric = :mah 
h = 1 ; k = 200 ; nlv = 4:20
model = lwplsravg(; nlvdis, metric, h, k, nlv) ;
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

res = predict(model, Xtest) ; 
@names res 
res.listnn
res.listd
res.listw
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction",  
    ylabel = "Observed").f  
```
