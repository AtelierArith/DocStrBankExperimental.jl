```
treer(; kwargs...)
treer(X, y; kwargs...)
```

回帰木 (CART) は DecisionTree.jl を使用しています。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量 yデータ (n)。

キーワード引数:

  * `n_subfeatures` : 各分割でランダムに選択する変数の数 (デフォルト: 0 ==> すべて保持)。
  * `max_depth` : 決定木の最大深さ (デフォルト: -1 ==> 最大なし)。
  * `min_sample_leaf` : 各葉が持つ必要がある最小サンプル数。
  * `min_sample_split` : 分割に必要な観測の最小数。
  * `scal` : ブール値。`true` の場合、`X` の各列はその未修正の標準偏差でスケーリングされます。

この関数は、パッケージ `DecisionTree.jl` を使用して単一の回帰木 (CART) をフィットさせます。

## 参考文献

Breiman, L., Friedman, J. H., Olshen, R. A., and Stone, C. J. Classification And Regression Trees. Chapman & Hall, 1984.

DecisionTree.jl https://github.com/JuliaAI/DecisionTree.jl

Gey, S., 2002. Bornes de risque, détection de ruptures, boosting : trois thèmes statistiques autour de CART en régression (These de doctorat). Paris 11. http://www.theses.fr/2002PA112245

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

n_subfeatures = p / 3 
max_depth = 15
model = treer(; n_subfeatures, max_depth) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction", 
    ylabel = "Observed").f    
```
