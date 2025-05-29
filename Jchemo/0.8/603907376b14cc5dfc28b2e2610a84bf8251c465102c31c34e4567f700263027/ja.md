```
plotgrid(indx::AbstractVector, r; size = (500, 300), step = 5, 
    color = nothing, kwargs...)
plotgrid(indx::AbstractVector, r, group; size = (700, 350), 
    step = 5, color = nothing, leg = true, leg_title = "Group", kwargs...)
```

モデルの誤差/パフォーマンス率をプロットします。

  * `indx` : モデルパラメータのグリッドを表す数値変数。例えば、PLSRモデルのLVの数。
  * `r` : 誤差/パフォーマンス率。

キーワード引数:

  * `group` : グループを定義するカテゴリ変数。`group`の各レベルに対して別々の線がプロットされます。
  * `size` : 図のサイズ（横、縦）。
  * `step` : xticksを定義するために使用されるステップ。
  * `color` : 色を設定します。`group`が使用される場合、`group`のレベル数と同じ長さのベクトルでなければなりません。
  * `leg` : ブール値。`group`が使用される場合、凡例を表示するかどうか。
  * `leg_title` : 凡例のタイトル。
  * `kwargs` : CairoMakieの`Axis`に渡すオプションの引数。

`plotgrid`を使用するには、バックエンド（例：CairoMakie）を指定する必要があります。

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

model = plskern() 
nlv = 0:20
res = gridscore(model, Xtrain, ytrain, 
    Xtest, ytest; score = rmsep, nlv)
plotgrid(res.nlv, res.y1; xlabel = "Nb. LVs", ylabel = "RMSEP").f

model = lwplsr() 
nlvdis = 15 ; metric = [:mah]
h = [1 ; 2.5 ; 5] ; k = [50 ; 100] 
pars = mpar(nlvdis = nlvdis, metric = metric, 
    h = h, k = k)
nlv = 0:20
res = gridscore(model, Xtrain, ytrain, Xtest, ytest; score = rmsep, 
    pars, nlv)
group = string.("h=", res.h, " k=", res.k)
plotgrid(res.nlv, res.y1, group; xlabel = "Nb. LVs", ylabel = "RMSECV").f
```
