```
rrr(; kwargs...)
rrr(X, Y; kwargs...)
rrr(X, Y, weights::Weight; kwargs...)
rr!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

縮小ランク回帰（RRR、別名RA）。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。`Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数（LV）の数。
  * `tau` : 正則化パラメータ (∊ [0, 1])。
  * `tol` : Nipalsアルゴリズムの許容誤差。
  * `maxit` : Nipalsアルゴリズムの最大反復回数。
  * `scal` : ブール値。`true`の場合、`X`と`Y`の各列はその未修正の標準偏差でスケーリングされます。

縮小ランク回帰は、冗長性分析（RA）回帰とも呼ばれます。この関数では、RAはMangamana et al 2021のセクション2.1.1で提示されたNipalsアルゴリズムを使用します。

連続正則化が利用可能です。ブロック中心化とスケーリングの後、共分散行列は次のように計算されます：

  * Cx = (1 - `tau`) * X'DX + `tau` * Ix

ここでDは観測（行）メトリックです。値`tau` = 0は共分散行列を逆転する際に不安定性を引き起こす可能性があります。一般的には、擬似逆行列と同様の結果を得るために、イプシロン値（例：`tau` = 1e-8）を使用する方が良い選択です。

## 参考文献

Bougeard, S., Qannari, E.M., Lupo, C., Chauvin, C., 2011. ユーザーの視点から見たマルチブロック冗長性分析。獣医学疫学への応用。電子応用統計分析ジャーナル 4, 203-214–214. https://doi.org/10.1285/i20705948v4n2p203

Bougeard, S., Qannari, E.M., Rose, N., 2011. マルチブロック冗長性分析：解釈ツールと疫学への応用。ケモメトリクスジャーナル 25, 467–475. https://doi.org/10.1002/cem.1392 

Tchandao Mangamana, E., Glèlè Kakaï, R., Qannari, E.M., 2021. マルチブロックデータ分析の監視手法を設定するための一般的戦略。ケモメトリクスとインテリジェントラボラトリーシステム 217, 104388. https://doi.org/10.1016/j.chemolab.2021.104388

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

nlv = 1
tau = 1e-4
model = rrr(; nlv, tau) 
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
```
