```
eposvd(D; nlv = 1)
```

スペクトルデータのキャリブレーション転送のための直交化行列を計算します。

  * `D` : スペクトル（行列Xの行）を直交化する必要がある有害情報を含むデータ（m, p）。

キーワード引数:

  * `nlv` : 直交化に考慮される`D`の最初のローディングベクトルの数。

目的は、Xデータセット（n, p）からいくつかの有害情報（例：信号の湿度パターン、複数の分光計など）を除去することです。有害情報は、行列`D`（m, p）から計算された主な行方向によって定義されます。

関数`eposvd`は2つのオブジェクトを返します：

  * `V` (p, `nlv`) : `D`のSVD分解（非中心化PCA）の最初の`nlv`ローディングベクトルの行列。
  * `M` (p, p) : 与えられた行列Xを`V`に含まれる方向に直交化するために使用される直交化行列。

任意の行列Xは次のようにして`D`から修正できます：

  * X_corrected = X * `M`。

行列`D`は多くの方法から構築できます。たとえば、2つの一般的な方法は次のとおりです：

  * EPO (Roger et al. 2003, 2018): `D`は異なる条件下で収集されたスペクトル間の差のセットから構築されます。
  * TOP (Andrew & Fearn 2004): `D`の各行は、特定の分光計器のために計算された平均スペクトルです。

特定の状況は次のとおりです。`D`が行列X1とX2の間のいくつかの差から構築され、双線形モデル（例：PLSR）がデータ{X1*corrected, Y}にフィットされていると仮定します。ここで、X1*corrected = X1 * `M`です。フィットされたモデルで新しいデータX2*newを予測するには、X2*newを修正する必要はありません。

# 参考文献

Andrew, A., Fearn, T., 2004. Transfer by orthogonal projection:  making near-infrared calibrations robust to between-instrument  variation. Chemometrics and Intelligent Laboratory Systems 72,  51–56. https://doi.org/10.1016/j.chemolab.2004.02.004

Roger, J.-M., Chauchard, F., Bellon-Maurel, V., 2003. EPO-PLS  external parameter orthogonalisation of PLS application to  temperature-independent measurement of sugar content of intact  fruits. Chemometrics and Intelligent Laboratory Systems 66,  191-204. https://doi.org/10.1016/S0169-7439(03)00051-0

Roger, J.-M., Boulet, J.-C., 2018. A review of orthogonal  projections for calibration. Journal of Chemometrics 32, e3045.  https://doi.org/10.1002/cem.3045

Zeaiter, M., Roger, J.M., Bellon-Maurel, V., 2006. Dynamic  orthogonal projection. A new method to maintain the on-line  robustness of multivariate calibrations. Application to NIR-based  monitoring of wine fermentations. Chemometrics and Intelligent  Laboratory Systems, 80, 227–235.  https://doi.org/10.1016/j.chemolab.2005.06.011

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

## 目的は、有害な 
## 情報（ここではD）をX1とX2の空間から除去することです
D = X1cal - X2cal
nlv = 2
res = eposvd(D; nlv)
res.M # 直交化行列
res.V # 有害な方向（行列Vの列 = Dのローディング）

## 修正されたVal行列
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
