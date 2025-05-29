```
detrend_arpls(; kwargs...)
detrend_arpls(X; kwargs...)
```

Xデータの各行のベースライン補正を非対称再加重ペナルティ最小二乗平滑化（ARPLS）によって行います。

  * `X` : Xデータ (n, p)。

キーワード引数:

  * `lb` : ペナルティ（滑らかさ）パラメータ "lambda"。
  * `tol` : 反復停止のための許容値。
  * `maxit` : 最大反復回数。
  * `verbose` : `true`の場合、反復回数が印刷されます。

デトレンド変換：この関数は、各観測値に対してARPLSを用いてベースラインをフィットさせ、残差（= ベースラインから補正された信号）を返します。

## 参考文献

Baek, S.-J., Park, A., Ahn, Y.-J., Choo, J., 2015. 非対称再加重ペナルティ最小二乗平滑化を用いたベースライン補正。Analyst 140, 250–257.  https://doi.org/10.1039/C4AN01061B

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

## 1つのスペクトルの例
i = 2
zX = Matrix(X)[i:i, :]
lb = 1e4
model = detrend_arpls(; lb, p)
fit!(model, zX)
zXc = transf(model, zX)   # = 補正されたスペクトル 
B = zX - zXc              # = 推定されたベースライン
f, ax = plotsp(zX, wl)
lines!(wl, vec(B); color = :blue)
lines!(wl, vec(zXc); color = :black)
f
```
