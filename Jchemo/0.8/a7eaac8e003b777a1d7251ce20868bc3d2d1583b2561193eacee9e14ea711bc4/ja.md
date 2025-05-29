```
mbplswest(; kwargs...)
mbplswest(Xbl, Y; kwargs...)
mbplswest(Xbl, Y, weights::Weight; kwargs...)
mbplswest!(Xbl::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

マルチブロックPLSR（MBPLSR） - Nipalsアルゴリズム。

  * `Xbl` : Xデータのブロックのリスト（行列のベクトル）    通常、（n, p）データの関数`mblock`の出力。
  * `Y` : Yデータ（n, q）。
  * `weights` : 観測値の重み（n）。    `Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 計算するグローバル潜在変数（LVs = スコア）の数。
  * `bscal` : ブロックスケーリングのタイプ。可能な値については関数`blockscal`を参照。
  * `tol` : 収束のための許容値（Nipals）。
  * `maxit` : 最大反復回数（Nipals）。
  * `scal` : ブール値。`true`の場合、`Xbl`および`Y`の各ブロックの列は、その未修正の標準偏差でスケーリングされます    （ブロックスケーリングの前に）。

この関数は、Westerhuis et al. 1998のようにMBPLSR Nipalsアルゴリズムを実装します。この関数は、関数`mbplsr`と同じグローバルスコアと予測を提供します。

関数`summary`は次のものを返します：

  * `explvarx` : グローバルLVによって説明される総X慣性（平方フロベニウスノルム）の割合。
  * `rvxbl2t` : 各ブロックとグローバルLVとの間のRV係数。
  * `rdxbl2t` : 各ブロック（= Xbl[k]）とグローバルLVとの間のRd係数。
  * `cortbl2t` : ブロックLV（= Tbl[k]）とグローバルLVとの間の相関。
  * `corx2t` : X変数とグローバルLVとの間の相関。

## 参考文献

Westerhuis, J.A., Kourti, T., MacGregor, J.F., 1998. マルチブロックおよび階層的PCAおよびPLSモデルの分析。化学計量学ジャーナル 12, 301–321.  https://doi.org/10.1002/(SICI)1099-128X(199809/10)12:5<301::AID-CEM515>3.0.CO;2-S

## 例

```julia
using Jchemo, JchemoData, JLD2
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "ham.jld2") 
@load db dat
@names dat 
X = dat.X
Y = dat.Y
y = Y.c1
group = dat.group
listbl = [1:11, 12:19, 20:25]
s = 1:6
Xbltrain = mblock(X[s, :], listbl)
Xbltest = mblock(rmrow(X, s), listbl)
ytrain = y[s]
ytest = rmrow(y, s) 
ntrain = nro(ytrain) 
ntest = nro(ytest) 
ntot = ntrain + ntest 
(ntot = ntot, ntrain , ntest)

nlv = 3
bscal = :frob
scal = false
#scal = true
model = mbplswest(; nlv, bscal, scal)
fit!(model, Xbltrain, ytrain)
@names model 
@names model.fitm
@head model.fitm.T
@head transf(model, Xbltrain)
transf(model, Xbltest)

res = predict(model, Xbltest)
res.pred 
rmsep(res.pred, ytest)

res = summary(model, Xbltrain) ;
@names res 
res.explvarx
res.rvxbl2t
res.rdxbl2t
res.cortbl2t
res.corx2t 
```
