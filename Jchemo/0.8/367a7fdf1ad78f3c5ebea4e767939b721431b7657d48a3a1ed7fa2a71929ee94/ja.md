```
savgol(; kwargs...)
savgol(X; kwargs...)
```

各行のXデータのSavitzky-Golay導出と平滑化。

  * `X` : Xデータ (n, p)。

キーワード引数:

  * `npoint` : フィルタのサイズ（カーネルに関与するポイント数）。奇数であり、3以上でなければなりません。半ウィンドウサイズはnhwindow = (`npoint` - 1) / 2です。
  * `deriv` : 導出の順序。0 <= `deriv` <= `degree`でなければなりません。
  * `degree` : 平滑化多項式の次数。1 <= `degree` <= `npoint` - 1でなければなりません。

平滑化は、ImageFiltering.jlパッケージの関数imfilterを使用して畳み込み（パディングあり）によって計算されます。返される各ポイントはカーネルの中心に位置します。カーネルは関数`savgk`を使用して計算されます。

この関数は行列(n, p)を返します。

## 参考文献

Luo, J., Ying, K., Bai, J., 2005. Savitzky–Golay smoothing and differentiation filter for even number data. Signal Processing 85, 1429–1434. https://doi.org/10.1016/j.sigpro.2005.02.002

Savitzky, A., Golay, M.J.E., 2002. Smoothing and Differentiation of Data by Simplified Least Squares Procedures. [WWW Document]. https://doi.org/10.1021/ac60214a047

Schafer, R.W., 2011. What Is a Savitzky-Golay Filter? [Lecture Notes]. IEEE Signal Processing Magazine 28, 111–117. https://doi.org/10.1109/MSP.2011.941097

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X
year = dat.Y.year
s = year .<= 2012
Xtrain = X[s, :]
Xtest = rmrow(X, s)
wlst = names(dat.X)
wl = parse.(Float64, wlst)
plotsp(X, wl; nsamp = 20).f

npoint = 11 ; deriv = 2 ; degree = 2
model = savgol(; npoint, deriv, degree) 
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
plotsp(Xptrain).f
plotsp(Xptest).f

####### ガウス信号 

u = -15:.1:15
n = length(u)
x = exp.(-.5 * u.^2) / sqrt(2 * pi) + .03 * randn(n)
M = 10  # 半ウィンドウ
N = 3   # 次数
deriv = 0
#deriv = 1
model = savgol(; npoint = 2M + 1, degree = N, deriv)
fit!(model, x')
xp = transf(model, x')
f, ax = plotsp(x', u; color = :blue)
lines!(ax, u, vec(xp); color = :red)
f
```
