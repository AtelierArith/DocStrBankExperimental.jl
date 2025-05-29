```
rfr(; kwargs...)
rfr(X, y; kwargs...)
```

DecisionTree.jlによるランダムフォレスト回帰。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量yデータ (n)。

キーワード引数：

  * `n_trees` : 森のために構築された木の数。
  * `partial_sampling` : 各木のためにサンプリングされた観測の割合。
  * `n_subfeatures` : 各分割でランダムに選択する変数の数 (デフォルト: -1 ==> sqrt(#variables))。
  * `max_depth` : 決定木の最大深さ (デフォルト: -1 ==> 最大なし)。
  * `min_sample_leaf` : 各葉が持つ必要がある最小サンプル数。
  * `min_sample_split` : 分割に必要な観測の最小数。
  * `mth` : 新しいデータが関数`predict`で予測されるときにマルチスレッドが行われるかどうかを示すブール値。
  * `scal` : ブール値。`true`の場合、`X`の各列はその未修正の標準偏差でスケーリングされる。

この関数は、パッケージ`DecisionTree.jl`を使用してランダムフォレスト回帰モデルを適合させます。

## 参考文献

Breiman, L., 1996. Bagging predictors. Mach Learn 24,  123–140. https://doi.org/10.1007/BF00058655

Breiman, L., 2001. Random Forests. Machine Learning  45, 5–32. https://doi.org/10.1023/A:1010933404324

DecisionTree.jl https://github.com/JuliaAI/DecisionTree.jl

Genuer, R., 2010. Forêts aléatoires : aspects théoriques,  sélection de variables et applications. PhD Thesis.  Université Paris Sud - Paris XI.

Gey, S., 2002. Bornes de risque, détection de ruptures,  boosting : trois thèmes statistiques autour de CART en  régression (These de doctorat). Paris 11.  http://www.theses.fr/2002PA112245

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
p = nco(X)

n_trees = 200
n_subfeatures = p / 3
max_depth = 15
model = rfr(; n_trees, n_subfeatures, max_depth) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction", 
    ylabel = "Observed").f    
```
