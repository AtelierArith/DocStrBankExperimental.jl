```
difmean(X1, X2; normx::Bool = false)
```

2つのXデータの列平均の差によって1次元の有害行列を計算します。

  * `X1` : スペクトル (n1, p)。
  * `X2` : スペクトル (n2, p)。

キーワード引数:

  * `normx` : ブール値。`true`の場合、`X1`と`X2`の列平均ベクトルは、その差を計算する前に正規化されます。

この関数は、2つの平均スペクトル、すなわち`X1`と`X2`の列平均の間の差によって計算された行列`D` (1, p) を返します。

`D`は、キャリブレーション転送のために`X1`と`X2`から除去できる有害な情報を含むと想定されています。たとえば、`D`は関数`eposvd`の入力として使用できます。

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/caltransfer.jld2")
@load db dat
@names dat
X1cal = dat.X1cal
X1val = dat.X1val
X2cal = dat.X2cal
X2val = dat.X2val

## 目的は、空間X1とX2から有害な
## 情報（ここではD）を除去することです
D = difmean(X1cal, X2cal).D
res = eposvd(D; nlv = 1)
## 補正されたVal行列
X1val_c = X1val * res.M
X2val_c = X2val * res.M

i = 1
f = Figure(size = (800, 300))
ax1 = Axis(f[1, 1])
ax2 = Axis(f[1, 2])
lines!(ax1, X1val[i, :]; label = "x1")
lines!(ax1, X2val[i, :]; label = "x2")
axislegend(ax1, position = :cb, framevisible = false)
lines!(ax2, X1val_c[i, :]; label = "x1_correct")
lines!(ax2, X2val_c[i, :]; label = "x2_correct")
axislegend(ax2, position = :cb, framevisible = false)
f
```
