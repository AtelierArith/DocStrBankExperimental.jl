```
rfda(; kwargs...)
rfda(X, y::Union{Array{Int}, Array{String}}; kwargs...)
```

DecisionTree.jlによるランダムフォレスト識別。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。

キーワード引数：

  * `n_trees` : 森のために構築された木の数。
  * `partial_sampling` : 各木のためにサンプリングされた観測の割合。
  * `n_subfeatures` : 各分割でランダムに選択する変数の数 (デフォルト: -1 ==> sqrt(#variables))。
  * `max_depth` : 決定木の最大深さ (デフォルト: -1 ==> 制限なし)。
  * `min_sample_leaf` : 各葉が持つ必要がある最小サンプル数。
  * `min_sample_split` : 分割に必要な観測の最小数。
  * `mth` : 新しいデータが関数`predict`で予測されるときにマルチスレッドが行われるかどうかを示すブール値。
  * `scal` : ブール値。`true`の場合、`X`の各列はその未修正の標準偏差でスケーリングされる。

この関数は、パッケージ`DecisionTree.jl`を使用してランダムフォレスト識別²モデルを適合させます。

DecisionTree.jlにおけるDAでは、'y'の成分はIntまたはStringでなければなりません。

## 参考文献

Breiman, L., 1996. Bagging predictors. Mach Learn 24,  123–140. https://doi.org/10.1007/BF00058655

Breiman, L., 2001. Random Forests. Machine Learning  45, 5–32. https://doi.org/10.1023/A:1010933404324

DecisionTree.jl https://github.com/JuliaAI/DecisionTree.jl

Genuer, R., 2010. Forêts aléatoires : aspects théoriques,  sélection de variables et applications. PhD Thesis.  Université Paris Sud - Paris XI.

Gey, S., 2002. Bornes de risque, détection de ruptures,  boosting : trois thèmes statistiques autour de CART en  régression (These de doctorat). Paris 11.  http://www.theses.fr/2002PA112245

## 例

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/forages2.jld2")
@load db dat
@names dat
X = dat.X
Y = dat.Y
n, p = size(X) 
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

n_trees = 200
n_subfeatures = p / 3 
max_depth = 10
model = rfda(; n_trees, n_subfeatures, max_depth) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
fitm = model.fitm ;
fitm.lev
fitm.ni

res = predict(model, Xtest) ; 
@names res 
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt
```
