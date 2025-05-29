```
plotsp(X, wl = 1:nco(X); size = (500, 300), color = nothing, nsamp = nothing, 
    kwargs...)
```

スペクトルをプロットします。

  * `X` : Xデータ (n, p)。
  * `wl` : `X`の列名。数値である必要があります。

キーワード引数:

  * `size` : 図のサイズ (横, 縦)。
  * `color` : スペクトルにユニークな色 (および最終的には透明度) を設定します。
  * `nsamp` : プロットするスペクトルの数 (Xの行)。`nothing`の場合、すべてのスペクトルがプロットされます。
  * `kwargs` : CairoMakieの`Axis`に渡すオプションの引数。

この関数は`X`の行をプロットします。

`plotxy`を使用するには、バックエンド (例: CairoMakie) を指定する必要があります。

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X
wlst = names(X)
wl = parse.(Float64, wlst) 

plotsp(X).f
plotsp(X; color = (:red, .2)).f
plotsp(X, wl; xlabel = "波長 (nm)", ylabel = "吸光度").f

tck = collect(wl[1]:200:wl[end]) ;
plotsp(X, wl; xlabel = "波長 (nm)", ylabel = "吸光度", xticks = tck).f

f, ax = plotsp(X, wl; color = (:red, .2))
xmeans = colmean(X)
lines!(ax, wl, xmeans; color = :black, linewidth = 2)
vlines!(ax, 1200)
f
```
