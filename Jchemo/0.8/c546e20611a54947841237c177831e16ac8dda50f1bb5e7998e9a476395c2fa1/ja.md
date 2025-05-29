```
occod(; kwargs...)
occod(fitm, X; kwargs...)
```

PCA/PLS直交距離（OD）を使用した一クラス分類。

  * `fitm` : トレーニングデータにフィットし、トレーニングクラスを表すと想定される予備モデル（例：関数`pcasvd`によって返されるオブジェクト`fitm`）。
  * `X` : モデル`fitm`がフィットしたトレーニングXデータ（n, p）。

キーワード引数：

  * `cut` : カットオフのタイプ。可能な値は：`:mad`, `:q`。詳細は後述。
  * `cri` : `cut` = `:mad`のときの定数。詳細は後述。
  * `risk` : `cut` = `:q`のときのリスク-Iレベル。詳細は後述。

このメソッドでは、観測値の外れ値度合い`d`は、この観測値の直交距離（= 'X残差'）であり、すなわち、観測値とフィットした（例：PCA）モデルによって定義されたスコア平面上のその投影との間のユークリッド距離です（例：Hubert et al. 2005, Van Branden & Hubert 2005 p. 66, Varmuza & Filzmoser 2009 p. 79）。

出力の詳細については、関数`occsd`を参照してください。

## 参考文献

M. Hubert, V. J. Rousseeuw, K. Vanden Branden (2005). ROBPCA: robust主成分分析への新しいアプローチ。Technometrics, 47, 64-79。

K. Vanden Branden, M. Hubert (2005). SIMCA法に基づく高次元でのロバスト分類。Chem. Lab. Int. Syst, 79, 10-21。

K. Varmuza, V. Filzmoser (2009). ケモメトリクスにおける多変量統計分析の入門。CRC Press, Boca Raton。

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
## - cla_trainは参照クラス（'in'）
## - cla_testは予測される観測値（cla_trainの'in'または'out'になるべき）
## 以下、cla_train = "EEH"、cla_testの2つの例状況：
cla_train = "EHH" ; cla_test = "PEE" ; typtest = "out"   # ここでcla_testは'out'として検出されるべき
#cla_train = "EHH" ; cla_test = "EHH" ; typtest = "in"   # ここでcla_testは'out'として検出されるべきではない
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
model = occod()
#model = occod(cut = :mad, cri = 4)
#model = occod(cut = :q, risk = .01)
#model = occsdod()
fit!(model, model_lv.fitm, zXtrain) 
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
