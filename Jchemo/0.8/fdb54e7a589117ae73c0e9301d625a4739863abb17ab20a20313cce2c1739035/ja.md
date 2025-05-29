```
mbpca(; kwargs...)
mbpca(Xbl; kwargs...)
mbpca(Xbl, weights::Weight; kwargs...)
mbpca!(Xbl::Matrix, weights::Weight; kwargs...)
```

コンセンサス主成分分析（CPCA、別名MBPCA）。

  * `Xbl` : Xデータのブロックのリスト（行列のベクトル）。    通常、関数`mblock`の出力です。
  * `weights` : 観測値の重み（n）。    `Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 計算するグローバル潜在変数（LVs = スコア）の数。
  * `bscal` : ブロックスケーリングのタイプ。可能な値については関数`blockscal`を参照してください。
  * `tol` : Nipals収束のための許容値。
  * `maxit` : 最大反復回数（Nipals）。
  * `scal` : ブール値。`true`の場合、`Xbl`のブロックの各列はその未修正の標準偏差でスケーリングされます（ブロックスケーリングの前に）。

CPCAアルゴリズム（Westerhuis et al; 1998）、別名MBPCA、Smilde et al. 2003ではCPCA-Wと呼ばれています。

最終的なブロックスケーリングを除けば、MBPCAは水平方向に連結された行列X = [X1 X2 ... Xk]のPCAに相当します（Smilde et al 2003のSUM-PCA）。

この関数は、特に以下のいくつかのオブジェクトを返します：

  * `T` : グローバルLVs（ノルムなし）。
  * `U` : グローバルLVs（ノルムあり）。
  * `W` : ブロック重み（ノルムあり）。
  * `Tb` : ブロックLVs（メトリックスケール）、**LVごとにグループ化**して返されます。
  * `Tbl` : ブロックLVs（元のスケール）、**ブロックごとにグループ化**して返されます。
  * `Vbl` : ブロック負荷（ノルムあり）。
  * `lb` : グローバルLVsのためのブロック特有の重み（'lambda'）。
  * `mu` : グローバルPCAの固有値に相当するブロック特有の重みの合計。

関数`summary`は以下を返します：

  * `explvarx` : グローバルLVsによって説明される総X慣性（平方フロベニウスノルム）の割合。
  * `explxbl` : グローバルLVsによって説明される各ブロック（= Xbl[k]）の慣性の割合。
  * `contrxbl2t` : グローバルLVsへの各ブロックの寄与（= lbの割合）。
  * `rvxbl2t` : 各ブロックとグローバルLVsとの間のRV係数。
  * `rdxbl2t` : 各ブロックとグローバルLVsとの間のRd係数。
  * `cortbl2t` : ブロックLVs（= Tbl[k]）とグローバルLVsとの間の相関。
  * `corx2t` : X変数とグローバルLVsとの間の相関。

## 参考文献

Mangamana, E.T., Cariou, V., Vigneau, E., Glèlè Kakaï, R.L.,  Qannari, E.M., 2019. 無監督マルチブロックデータ分析：統一アプローチと拡張。化学計測およびインテリジェントラボラトリーシステム 194, 103856.  https://doi.org/10.1016/j.chemolab.2019.103856

Smilde, A.K., Westerhuis, J.A., de Jong, S., 2003. 逐次マルチブロック成分法のためのフレームワーク。化学計測ジャーナル 17, 323–337.  https://doi.org/10.1002/cem.811

Westerhuis, J.A., Kourti, T., MacGregor, J.F., 1998. マルチブロックおよび階層的PCAおよびPLSモデルの分析。化学計測ジャーナル 12, 301–321.  https://doi.org/10.1002/(SICI)1099-128X(199809/10)12:5<301::AID-CEM515>3.0.CO;2-S

## 例

```julia
using Jchemo, JchemoData, JLD2
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "ham.jld2") 
@load db dat
@names dat 
X = dat.X
group = dat.group
listbl = [1:11, 12:19, 20:25]
Xbl = mblock(X[1:6, :], listbl)
Xblnew = mblock(X[7:8, :], listbl)
n = nro(Xbl[1]) 

nlv = 3
bscal = :frob
scal = false
#scal = true
model = mbpca(; nlv, bscal, scal)
fit!(model, Xbl)
@names model 
@names model.fitm
## グローバルスコア 
@head model.fitm.T
@head transf(model, Xbl)
transf(model, Xblnew)
## ブロックスコア
i = 1
@head model.fitm.Tbl[i]
@head transfbl(model, Xbl)[i]

res = summary(model, Xbl) ;
@names res 
res.explvarx
res.explxbl   # = model.fitm.lb if bscal = :frob
rowsum(Matrix(res.explxbl))
res.contrxbl2t
res.rvxbl2t
res.rdxbl2t
res.cortbl2t
res.corx2t 
```
