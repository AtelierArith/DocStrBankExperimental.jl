```
mavg(; kwargs...)
mavg(X; kwargs...)
```

Xデータの各行の移動平均による平滑化。

  * `X` : Xデータ (n, p)。

キーワード引数:

  * `npoint` : ウィンドウに関与するポイント数。

この関数は行列 (n, p) を返します。

平滑化は、ImageFiltering.jl パッケージの `imfilter` 関数を使用して、パディングを伴う畳み込みによって計算されます。中心のカーネルは `ones(npoint) / npoint` です。返される各ポイントはカーネルの中心に位置します。信号 x の長さ p (X の行) に対応する p 波長 (または他のインデックス) のベクトル wl を仮定します。

`npoint = 3` の場合、カーネルは kern = [.33, .33, .33] であり:

  * インデックス i = 4 の出力値は: dot(kern, [x[3], x[4], x[5]]) です。出力波長は: wl[4]
  * インデックス i = 1 の出力値は: dot(kern, [x[1], x[1], x[2]])    (パディング)。対応する波長は: wl[1] です。

`npoint = 4` の場合、カーネルは kern = [.25, .25, .25, .25] であり:

  * インデックス i = 4 の出力値は: dot(kern, [x[3], x[4], x[5], x[6]]) です。対応する波長は: (wl[4] + wl[5]) / 2 です。
  * インデックス i = 1 の出力値は: dot(kern, x[1], x[1], x[2], x[3])    (パディング)。対応する波長は: (wl[1] + wl[2]) / 2 です。

## 参考文献

パッケージ ImageFiltering.jl https://github.com/JuliaImages/ImageFiltering.jl

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

model = mavg(npoint = 10) 
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
plotsp(Xptrain).f
plotsp(Xptest).f
```
