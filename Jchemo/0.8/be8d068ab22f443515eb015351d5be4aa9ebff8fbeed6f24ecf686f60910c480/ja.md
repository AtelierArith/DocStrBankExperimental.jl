```
pcapp(; kwargs...)
pcapp(X; kwargs...)
pcapp!(X::Matrix; kwargs...)
```

投影追求によるロバストPCA。

  * `X` : Xデータ (n, p)。

キーワード引数：

  * `nlv` : 主成分 (PC) の数。
  * `nsim` : 投影追求のための追加のシミュレートされた方向の数 (X行に対して)。
  * `scal` : ブール値。`true` の場合、`X` の各列はそのMADでスケーリングされる。

`nsim = 0` の場合、これはCroux & Ruiz-Gazen (C-R, 2005) PCAアルゴリズムで、投影追求 (PP) メソッドを使用します。データ `X` は空間中央値によってロバストに中心化され、観測値は正規化された後に観測値 (Xの行) によって定義された「PP」方向に投影されます。最初のPCAローディングベクトルは、与えられた「投影指標」を最大化する方向 (PP方向内) であり、ここでは中央値絶対偏差 (MAD) です。次に、`X` はこのローディングベクトルに対してデフレートされ、次のローディングベクトルを定義するためにプロセスが再実行されます。以下同様です。

このアルゴリズムの可能な拡張は、n行の観測値に追加の候補PP方向をランダムにシミュレートすることです。`nsim > 0` の場合、関数は最初のn個のPP方向に対して `nsim` の追加PP方向をシミュレートします。これはHubert et al. (2005)で提案されたもので、`X` からランダムな観測値のペアがサンプリングされ、各ペアについて、その方向はペアの2つの観測値を通過します (関数 `simpphub` を参照)。

## 参考文献

Croux, C., Ruiz-Gazen, A., 2005. 主成分のための高いブレークダウン推定量：投影追求アプローチの再考。Journal of Multivariate Analysis 95, 206–226.  https://doi.org/10.1016/j.jmva.2004.08.002

Hubert, M., Rousseeuw, V.J., Vanden Branden, K., 2005. ROBPCA: ロバスト主成分分析への新しいアプローチ。Technometrics 47, 64-79. https://doi.org/10.1198/004017004000000563

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie 
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "octane.jld2") 
@load db dat
@names dat
X = dat.X 
wlst = names(X)
wl = parse.(Float64, wlst)
n = nro(X)

nlv = 3
model = pcapp(; nlv, nsim = 2000)  
#model = pcasvd(; nlv) 
fit!(model, X)
@names model
@names model.fitm
@head T = model.fitm.T
## 同じ：
@head transf(model, X)

i = 1
plotxy(T[:, i], T[:, i + 1]; zeros = true, xlabel = string("PC", i), 
    ylabel = string("PC", i + 1)).f
```
