```
winvs(d; h = 2, criw = 4, squared = false)
winvs!(d; h = 2, criw = 4, squared = false)
```

距離から重みを逆スケーリング指数関数を使用して計算します。

  * `d` : 距離のベクトル。

キーワード引数:

  * `h` : 重み関数の形状を定義するスケーリングの正のスカラー。
  * `criw` : 距離ベクトル `d` の外れ値を定義する正のスカラー。
  * `squared`: `true` の場合、距離は二乗距離に置き換えられます; 重み関数はガウス（RBF）カーネル関数になります。

重みは次のように計算されます:

  * exp(-`d` / (`h` * MAD(`d`)))

または、`d` > Median(`d`) + criw * MAD(`d`) のような極端（潜在的に外れ値）の距離に対しては0に設定されます。最後に、重みはその最大値に標準化されます。これは、Kim et al. 2011で提示された重み関数の適応です。

距離が増加すると重みは減少します。`h` が小さいほど、減少関数は鋭くなります。

## 参考文献

Kim S, Kano M, Nakagawa H, Hasebe S. Estimation of active pharmaceutical ingredients content using locally  weighted partial least squares and statistical wavelength selection. Int J Pharm. 2011; 421(2):269-274. https://doi.org/10.1016/j.ijpharm.2011.10.007

## 例

```julia
using Jchemo, CairoMakie, Distributions

x1 = rand(Chisq(10), 100) ;
x2 = rand(Chisq(40), 10) ;
d = [sqrt.(x1) ; sqrt.(x2)]
h = 2 ; criw = 3
w = winvs(d; h, criw) ;
f = Figure(size = (600, 300))
ax1 = Axis(f, xlabel = "Distance", ylabel = "Nb. observations")
hist!(ax1, d, bins = 30)
ax2 = Axis(f, xlabel = "Distance", ylabel = "Weight")
scatter!(ax2, d, w)
f[1, 1] = ax1 
f[1, 2] = ax2 
f

d = collect(0:.5:15) ;
h = [.5, 1, 1.5, 2.5, 5, 10, Inf] 
#w = winvs(d; h = h[1]) 
f = Figure(size = (500, 400))
ax = Axis(f, xlabel = "Distance", ylabel = "Weight")
lines!(ax, d, w, label = string("h = ", h[1]))
for i = 2:length(h)
    w = winvs(d; h = h[i])
    lines!(ax, d, w, label = string("h = ", h[i]))
end
axislegend("Values of h"; position = :lb)
f[1, 1] = ax
f
```
