```
occsd(; kwargs...)
occsd(fitm; kwargs...)
```

PCA/PLSスコア距離（SD）を使用した一クラス分類。

  * `fitm` : トレーニングデータにフィットし、トレーニングクラスを表すと想定される予備モデル（例：関数`pcasvd`によって返されるオブジェクト`fitm`）。

キーワード引数：

  * `cut` : カットオフのタイプ。可能な値は： `:mad`, `:q`。詳細は後述。
  * `cri` : `cut` = `:mad` の場合、定数。詳細は後述。
  * `risk` : `cut` = `:q` の場合、リスク-Iレベル。詳細は後述。

このメソッドでは、観測値の外れ値度合い `d` は、そのスコア距離（SD）によって定義されます。つまり、観測値のスコアプラン上の投影とスコアプランの「中心」（常にゼロで定義される）との間のマハラノビス距離です。

新しい観測値の `d` が与えられた `cutoff` よりも高い場合、その観測値はトレーニング（= 参照）クラスに属さないと見なされます。`cutoff` は非パラメトリックなヒューリスティックを用いて計算されます。トレーニングクラスで計算された外れ値度合いのベクトルを [d] とします：

  * `cut` = `:mad` の場合、`cutoff` = median([d]) + `cri` * madv([d])。
  * `cut` = `:q` の場合、`cutoff` は [d] に基づいて計算された経験的累積分布関数から推定されます。与えられたリスク-I（`risk`）に対して。

文献では、代替の近似カットオフが提案されています（例：Nomikos & MacGregor 1995, Hubert et al. 2005, Pomerantsev 2008）。通常、カットオフを計算するために使用される近似手法に関係なく、検出目的に応じてこのカットオフを調整することが推奨されます。

**出力**

  * `pval`: トレーニング分布 [d] から計算された p 値の推定（関数 `pval` を参照）。
  * `dstand`: `d` / `cutoff` として定義される標準化距離。`dstand` > 1 の値は、トレーニングデータの分布と比較して極端と見なされる可能性があります。
  * `gh` は Winisi の "GH"（通常、GH > 3 は極端と見なされます）。

関数 `predict` に特有：

  * `pred`: クラス予測

      * `dstand` <= 1 ==> `in`: 観測値はトレーニングクラスに属すると予想されます。
      * `dstand` > 1  ==> `out`: 極端な値であり、トレーニングと同じクラスに属さない可能性があります。

## 参考文献

M. Hubert, V. J. Rousseeuw, K. Vanden Branden (2005). ROBPCA: robust主成分分析への新しいアプローチ。Technometrics, 47, 64-79。

Nomikos, V., MacGregor, J.F., 1995. バッチプロセスの監視のための多変量SPCチャート。null 37, 41-59。 https://doi.org/10.1080/00401706.1995.10485888

Pomerantsev, A.L., 2008. 投影法によって導出された多変量分類の受け入れ領域。Journal of Chemometrics 22, 601-609。 https://doi.org/10.1002/cem.1147

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/challenge2018.jld2") 
@load db dat
@names dat
X = dat.X    
Y = dat.Y
model = savgol(npoint = 21, deriv = 2, degree = 3)
fit!(model, X) 
Xp = transf(model, X) 
s = Bool.(Y.test)
Xtrain = rmrow(Xp, s)
Ytrain = rmrow(Y, s)
Xtest = Xp[s, :]
Ytest = Y[s, :]

## 例データの構築
## - cla_train は参照クラス（'in'）
## - cla_test には予測される観測値が含まれます（cla_train の 'in' または 'out'）
## 以下、cla_train = "EEH"、cla_test の2つの例状況：
cla_train = "EHH" ; cla_test = "PEE" ; typtest = "out"   # ここで cla_test は 'out' として検出されるべき
#cla_train = "EHH" ; cla_test = "EHH" ; typtest = "in"   # ここで cla_test は 'out' として検出されるべきではない
s = Ytrain.typ .== cla_train
zXtrain = Xtrain[s, :]    
s = Ytest.typ .== cla_test
zXtest = Xtest[s, :] 
ntrain = nro(zXtrain)
ntest = nro(zXtest)
ntot = ntrain + ntest
(ntot = ntot, ntrain, ntest)
ytrain = repeat(["in"], ntrain)
ytest = repeat([typtest], ntest)
## 終了

#### 予備PCAフィットモデル
nlv = 20
model_lv = pcasvd(; nlv) 
#model_lv = pcaout(; nlv) 
fit!(model_lv, zXtrain) 
res = summary(model_lv, zXtrain).explvarx 
plotgrid(res.nlv, res.pvar; step = 2, xlabel = "Nb. LVs", ylabel = "% Variance explained").f
Ttrain = model_lv.fitm.T
Ttest = transf(model_lv, zXtest)
T = vcat(Ttrain, Ttest)
i = 1
group = vcat(repeat(["Train"], ntrain), repeat(["Test"], ntest))
plotxy(T[:, i], T[:, i + 1], group; leg_title = "Class", xlabel = string("LV", i), 
    ylabel = string("LV", i + 1)).f

#### Occ
model = occsd()
#model = occsd(cut = :mad, cri = 4)
#model = occsd(cut = :q, risk = .01)
fit!(model, model_lv.fitm) 
@names model 
@names model.fitm 
@head dtrain = model.fitm.d
d = dtrain.dstand
f, ax = plotxy(1:length(d), d; size = (500, 300), xlabel = "Obs. index", 
    ylabel = "Standardized distance")
hlines!(ax, 1; linestyle = :dot)
f
## 予測
res = predict(model, zXtest) 
@names res
@head pred = res.pred
@head dtest = res.d
tab(pred)
errp(pred, ytest)
conf(pred, ytest).cnt
##
d = vcat(dtrain.dstand, dtest.dstand)
f, ax = plotxy(1:length(d), d, group; size = (500, 300), leg_title = "Class", xlabel = "Obs. index", 
    ylabel = "Standardized distance")
hlines!(ax, 1; linestyle = :dot)
f
```
