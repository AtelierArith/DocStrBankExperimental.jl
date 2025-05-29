```
occstah(; kwargs...)
occstah(X; kwargs...)
```

スタヘル-ドノホ外れ値を使用した一クラス分類。

  * `X` : トレーニング X データ (n, p)。

キーワード引数:

  * `nlv` : `X` が投影されるランダム方向の数。
  * `cut` : カットオフのタイプ。可能な値は: `:mad`, `:q`。詳細は後述。
  * `cri` : `cut` = `:mad` の場合、定数。詳細は後述。
  * `risk` : `cut` = `:q` の場合、リスク-I レベル。詳細は後述。
  * `scal` : ブール値。`true` の場合、`X` の各列は関数 `outstah` のようにスケーリングされる。

このメソッドでは、特定の観測値の外れ値度 `d` はスタヘル-ドノホ外れ値 (詳細は `?outstah` を参照) です。

出力の詳細については関数 `occsd` を参照してください。

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

## 以下、参照クラスは "EEH"
cla1 = "EHH" ; cla2 = "PEE" ; cod = "out"   # ここで cla2 は検出されるべき
#cla1 = "EHH" ; cla2 = "EHH" ; cod = "in"   # ここで cla2 は検出されるべきではない
s1 = Ytrain.typ .== cla1
s2 = Ytest.typ .== cla2
zXtrain = Xtrain[s1, :]    
zXtest = Xtest[s2, :] 
ntrain = nro(zXtrain)
ntest = nro(zXtest)
ntot = ntrain + ntest
(ntot = ntot, ntrain, ntest)
ytrain = repeat(["in"], ntrain)
ytest = repeat([cod], ntest)

## グループの説明
model = pcasvd(nlv = 10) 
fit!(model, zXtrain) 
Ttrain = model.fitm.T
Ttest = transf(model, zXtest)
T = vcat(Ttrain, Ttest)
group = vcat(repeat(["1"], ntrain), repeat(["2"], ntest))
i = 1
plotxy(T[:, i], T[:, i + 1], group; leg_title = "クラス", xlabel = string("PC", i),  
    ylabel = string("PC", i + 1)).f

#### Occ
model_occ = occstah(; nlv = 5000, scal = true)
fit!(model_occ, zXtrain) 
@names model_occ 
@names model_occ.fitm 
@head model_occ.fitm.V  # ランダム方向 
@head d = model_occ.fitm.d
d = d.dstand
f, ax = plotxy(1:length(d), d; size = (500, 300), xlabel = "観測値インデックス", 
    ylabel = "標準化距離")
hlines!(ax, 1; linestyle = :dot)
f

res = predict(model_occ, zXtest) ;
@names res
@head res.d
@head res.pred
tab(res.pred)
errp(res.pred, ytest)
conf(res.pred, ytest).cnt
d1 = model_occ.fitm.d.dstand
d2 = res.d.dstand
d = vcat(d1, d2)
f, ax = plotxy(1:length(d), d, group; size = (500, 300), leg_title = "クラス", 
    xlabel = "観測値インデックス", ylabel = "標準化距離")
hlines!(ax, 1; linestyle = :dot)
f
```
