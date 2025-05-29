```
rmgap(; kwargs...)
rmgap(X; kwargs...)
```

スペクトルの垂直ギャップを削除します（例：ASD用）。  

  * `X` : Xデータ (n, p)。

キーワード引数:

  * `indexcol` : ギャップを削除する`X`列のインデックス (∈ [1, p])。
  * `npoint` : 各ギャップの左側で線形回帰をフィッティングするために使用される`X`列の数。

各スペクトル（行観測の行列`X`）および各定義されたギャップについて、修正はギャップの左側で計算された単純な線形回帰からの外挿によって行われます。

例えば、列インデックス651-652の間と列インデックス1425-1426の間にそれぞれ2つのギャップが観察される場合、構文は`indexcol` = [651 ; 1425]となります。

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/asdgap.jld2") 
@load db dat
@names dat
X = dat.X
wlst = names(dat.X)
wl = parse.(Float64, wlst)

wl_target = [1000 ; 1800] 
indexcol = findall(in(wl_target).(wl))

f, ax = plotsp(X, wl)
vlines!(ax, wl_target; linestyle = :dot, color = (:grey, .8))
f

## 修正データ
model = rmgap(; indexcol, npoint = 5)
fit!(model, X)
Xc = transf(model, X)
f, ax = plotsp(Xc, wl)
vlines!(ax, wl_target; linestyle = :dot, color = (:grey, .8))
f
```
