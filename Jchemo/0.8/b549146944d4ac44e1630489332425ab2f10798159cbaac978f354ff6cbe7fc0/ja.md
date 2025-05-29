```
calds(; algo = plskern, kwargs...)
calds(X1, X2; algo = plskern, kwargs...)
```

スペクトルデータのキャリブレーション転送のための直接標準化（DS）。

  * `X1` : ターゲットに転送するスペクトル (n, p)。
  * `X2` : ターゲットスペクトル (n, p)。

キーワード引数：

  * `algo` : 転送モデルとして使用される関数。
  * `kwargs` : `algo` のためのオプション引数。

`X1` と `X2` は同じ n サンプル（「基準」）を表す必要があります。

目的は、スペクトル `X1` をターゲット `X2` にできるだけ近い新しいスペクトルに変換することです。メソッド DS は、`X1` から `X2` を予測するモデル（`algo` で定義）をフィットさせます。

## 参考文献

Y. Wang, D. J. Veltkamp, and B. R. Kowalski, “Multivariate Instrument Standardization,”  Anal. Chem., vol. 63, no. 23, pp. 2750–2756, 1991, doi: 10.1021/ac00023a016.

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/caltransfer.jld2")
@load db dat
@names dat
## オブジェクト X1 と X2 は同じサンプルで収集されたスペクトルです。 
## X2 はターゲット空間を表します。 
## X1 を X2 と同じ空間に転送したいです。
## 転送するデータ
X1cal = dat.X1cal
X1val = dat.X1val
n = nro(X1cal)
m = nro(X1val)
## ターゲット空間
X2cal = dat.X2cal
X2val = dat.X2val

## モデルのフィッティング
fitm = calds(X1cal, X2cal; algo = plskern, nlv = 10) 
#fitm = calds(X1cal, X2cal; algo = mlrpinv)   # よりロバストではない 

## 新しいスペクトル X1val の転送 
## X2val に近いことが期待される
pred = predict(fitm, X1val).pred

i = 1
f = Figure(size = (500, 300))
ax = Axis(f[1, 1])
lines!(X2val[i, :]; label = "x2")
lines!(ax, X1val[i, :]; label = "x1")
lines!(pred[i, :]; linestyle = :dash, label = "x1_corrected")
axislegend(position = :rb, framevisible = false)
f
```
