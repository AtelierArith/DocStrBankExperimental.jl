```
comdim(; kwargs...)
comdim(Xbl; kwargs...)
comdim(Xbl, weights::Weight; kwargs...)
comdim!(Xbl::Matrix, weights::Weight; kwargs...)
```

共通成分および特定の重み分析 (CCSWA、別名 ComDim)。

  * `Xbl` : Xデータのブロックのリスト（行列のベクトル）。    通常、関数 `mblock` の出力です。
  * `weights` : 観測の重み (n)。    `Weight` 型でなければなりません（例：関数 `mweight` を参照）。

キーワード引数：

  * `nlv` : 計算するグローバル潜在変数 (LVs = スコア) の数。
  * `bscal` : ブロックスケーリングのタイプ。可能な値については関数 `blockscal` を参照してください。
  * `tol` : 収束のための許容値 (Nipals)。
  * `maxit` : 最大反復回数 (Nipals)。
  * `scal` : ブール値。`true` の場合、`Xbl` の各ブロックの列は、    ブロックスケーリングの前にその未修正の標準偏差でスケーリングされます。

Hannafi & Qannari 2008 p.84 の "SVD" アルゴリズム。

この関数は、特に以下のいくつかのオブジェクトを返します：

  * `T` : グローバル LV (ノルムなし)。
  * `U` : グローバル LV (ノルムあり)。
  * `W` : ブロック重み (ノルムあり)。
  * `Tb` : ブロック LV (メトリックスケール)、**LVごとにグループ化**して返されます。
  * `Tbl` : ブロック LV (元のスケール)、**ブロックごとにグループ化**して返されます。
  * `Vbl` : ブロック負荷 (ノルムあり)。
  * `lb` : ブロック特定の重み (サリエンス) 'lambda'。
  * `mu` : ブロック特定の重みの合計。

関数 `summary` は以下を返します：

  * `explvarx` : グローバル LV によって説明される総 X 慣性 (二乗フロベニウスノルム) の割合。
  * `explvarxx` : グローバル LV によって説明される総 XX' 慣性の割合 (= Qannari et al. 2000、Hanafi et al. 2008 の指標 "V")。
  * `explxbl` : グローバル LV によって説明される各ブロック (= Xbl[k]) の慣性の割合。
  * `psal2` : 各グローバルスコア内の各ブロックの二乗サリエンスの割合。
  * `contrxbl2t` : グローバル LV への各ブロックの寄与 (= lb の割合)。
  * `rvxbl2t` : 各ブロックとグローバル LV との間の RV 係数。
  * `rdxbl2t` : 各ブロックとグローバル LV との間の Rd 係数。
  * `cortbl2t` : ブロック LV (= Tbl[k]) とグローバル LV との間の相関。
  * `corx2t` : X変数とグローバル LV との間の相関。

## 参考文献

Cariou, V., Qannari, E.M., Rutledge, D.N., Vigneau, E., 2018.  ComDim: From multiblock data analysis to path modeling. Food  Quality and Preference, Sensometrics 2016: Sensometrics-by-the-Sea  67, 27–34. https://doi.org/10.1016/j.foodqual.2017.02.012

Cariou, V., Jouan-Rimbaud Bouveresse, D., Qannari, E.M.,  Rutledge, D.N., 2019. Chapter 7 - ComDim Methods for the Analysis  of Multiblock Data in a Data Fusion Perspective, in: Cocchi, M. (Ed.),  Data Handling in Science and Technology,  Data Fusion Methodology and Applications. Elsevier, pp. 179–204.  https://doi.org/10.1016/B978-0-444-63984-4.00007-7

Ghaziri, A.E., Cariou, V., Rutledge, D.N., Qannari, E.M., 2016.  Analysis of multiblock datasets using ComDim: Overview and extension  to the analysis of (K + 1) datasets. Journal of Chemometrics 30,  420–429. https://doi.org/10.1002/cem.2810

Hanafi, M., 2008. Nouvelles propriétés de l’analyse en composantes  communes et poids spécifiques. Journal de la société française  de statistique 149, 75–97.

Qannari, E.M., Wakeling, I., Courcoux, P., MacFie, H.J.H., 2000.  Defining the underlying sensory dimensions. Food Quality and  Preference 11, 151–154.  https://doi.org/10.1016/S0950-3293(99)00069-5

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
model = comdim(; nlv, bscal, scal)
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
res.explvarxx
res.psal2 
res.contrxbl2t
res.explxbl   # = model.fitm.lb if bscal = :frob
rowsum(Matrix(res.explxbl))
res.rvxbl2t
res.rdxbl2t
res.cortbl2t
res.corx2t 
```
