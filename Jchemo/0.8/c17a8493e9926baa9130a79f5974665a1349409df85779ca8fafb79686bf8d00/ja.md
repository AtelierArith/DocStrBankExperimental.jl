```
plskern(; kwargs...)
plskern(X, Y; kwargs...)
plskern(X, Y, weights::Weight; kwargs...)
plskern!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

部分最小二乗回帰（PLSR）「改良カーネルアルゴリズム #1」（Dayal & McGegor, 1997）。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません（例えば、関数 `mweight` を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数（LV）の数。
  * `scal` : ブール値。`true` の場合、`X` と `Y` の各列はその未修正の標準偏差でスケーリングされます。

PLSアルゴリズムにおける行重み付け（`weights`）について：特にSchaal et al. 2002、Siccard & Sabatier 2006、Kim et al. 2011、Lesnoff et al. 2020を参照してください。

## 参考文献

Dayal, B.S., MacGregor, J.F., 1997. 改良PLSアルゴリズム。ジャーナル・オブ・ケモメトリックス 11, 73-85。

Kim, S., Kano, M., Nakagawa, H., Hasebe, S., 2011. ローカル加重部分最小二乗法と統計的波長選択を用いた活性医薬品成分含量の推定。国際薬学ジャーナル、421, 269-274。

Lesnoff, M., Metz, M., Roger, J.M., 2020. 農業NIRデータにおける回帰と識別のためのローカル加重PLS戦略の比較。ジャーナル・オブ・ケモメトリックス。e3209。 https://onlinelibrary.wiley.com/doi/abs/10.1002/cem.3209

Schaal, S., Atkeson, C., Vijayamakumar, S. 2002. リアルタイムロボット学習のための非パラメトリック統計からのスケーラブルな技術。応用知能、17, 49-60。

Sicard, E. Sabatier, R., 2006. ローカルPLS1回帰の理論的枠組みと降雨データセットへの応用。計算統計データ分析、51, 1393-1410。

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

nlv = 15
model = plskern(; nlv) ;
#model = plsnipals(; nlv) ;
#model = plswold(; nlv) ;
#model = plsrosa(; nlv) ;
#model = plssimp(; nlv) ;
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
@head model.fitm.T

coef(model)
coef(model; nlv = 3)

@head transf(model, Xtest)
@head transf(model, Xtest; nlv = 3)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "予測",  
    ylabel = "観測値").f    

res = predict(model, Xtest; nlv = 1:2)
@head res.pred[1]
@head res.pred[2]

res = summary(model, Xtrain) ;
@names res
z = res.explvarx
plotgrid(z.nlv, z.cumpvar; step = 2, xlabel = "潜在変数の数", 
    ylabel = "説明されたX分散の割合").f
```
