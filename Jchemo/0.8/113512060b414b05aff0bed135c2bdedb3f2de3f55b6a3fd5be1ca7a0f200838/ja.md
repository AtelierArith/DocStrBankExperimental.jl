```
plotxy(x, y; size = (500, 300), color = nothing, ellipse::Bool = false, 
    prob = .95, circle::Bool = false, bisect::Bool = false, zeros::Bool = false,
    xlabel = "", ylabel = "", title = "", kwargs...)
plotxy(x, y, group; size = (600, 350), color = nothing, ellipse::Bool = false, 
    prob = .95, circle::Bool = false, bisect::Bool = false, zeros::Bool = false,
    xlabel = "", ylabel = "", title = "", leg::Bool = true, leg_title = "Group", 
    kwargs...)
```

(x, y) データの散布図

  * `x` : xベクトル (n)。
  * `y` : yベクトル (n)。
  * `group` : グループを定義するカテゴリ変数 (n)。

キーワード引数:

  * `size` : 図のサイズ (横, 縦)。
  * `color` : 色を設定します。`group` が使用される場合、`color` は `group` のレベル数と同じ長さのベクトルでなければなりません。
  * `ellipse` : ブール値。信頼の楕円を描画します。自由度 df = 2 のカイ二乗分布を仮定します。`group` が使用される場合、グループごとに1つの楕円が描かれます。
  * `prob` : 信頼の楕円の確率。
  * `bisect` : ブール値。二等分線を描画します。
  * `zeros` : ブール値。原点 (0, 0) を通る水平および垂直軸を描画します。
  * `xlabel` : x軸のラベル。
  * `ylabel` : y軸のラベル。
  * `title` : グラフィックのタイトル。
  * `leg` : ブール値。`group` が使用される場合、凡例を表示するかどうか。
  * `leg_title` : 凡例のタイトル。
  * `kwargs` : Makie の `scatter` 関数に渡すオプション引数。

`plotxy` を使用するには、バックエンド (例: CairoMakie) を指定する必要があります。

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
lev = mlev(year)
nlev = length(lev)

model = pcasvd(nlv = 5)  
fit!(model, X) 
@head T = model.fitm.T

plotxy(T[:, 1], T[:, 2]; color = (:red, .5)).f

plotxy(T[:, 1], T[:, 2], year; ellipse = true, xlabel = "PC1", ylabel = "PC2").f

i = 2
colm = cgrad(:Dark2_5, nlev; categorical = true)
plotxy(T[:, i], T[:, i + 1], year; color = colm, xlabel = string("PC", i), 
    ylabel = string("PC", i + 1), zeros = true, ellipse = true).f

plotxy(T[:, 1], T[:, 2], year).lev

plotxy(1:5, 1:5).f

y = reshape(rand(5), 5, 1)
plotxy(1:5, y).f

## 複数のレイヤーを追加できます
## (Makie と同じ構文)
A = rand(50, 2)
f, ax = plotxy(A[:, 1], A[:, 2]; xlabel = "x1", ylabel = "x2")
ylims!(ax, -1, 2)
hlines!(ax, 0.5; color = :red, linestyle = :dot)
f
```
