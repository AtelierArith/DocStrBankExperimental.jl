```
mbplsr(; kwargs...)
mbplsr(Xbl, Y; kwargs...)
mbplsr(Xbl, Y, weights::Weight; kwargs...)
mbplsr!(Xbl::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

マルチブロックPLSR (MBPLSR)。

  * `Xbl` : Xデータのブロックのリスト（行列のベクトル）    通常、(n, p)データの関数`mblock`の出力。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。    `Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 計算するグローバル潜在変数の数 (LVs = スコア)。
  * `bscal` : ブロックスケーリングのタイプ。可能な値については関数`blockscal`を参照。
  * `scal` : ブール値。`true`の場合、`Xbl`および`Y`の各ブロックの列は、その未修正の標準偏差でスケーリングされます（ブロックスケーリングの前に）。

この関数は、{X, `Y`}に対してPLSRを実行します。ここでXは`Xbl`のブロックの水平連結です。この関数は、関数`mbplswest`と同じグローバルLVと予測を提供しますが、はるかに高速です。

関数`summary`は次のものを返します：

  * `explvarx` : グローバルLVによって説明される総X慣性（平方フロベニウスノルム）の割合。
  * `rvxbl2t` : 各ブロックとグローバルLVとの間のRV係数。
  * `rdxbl2t` : 各ブロック（= Xbl[k]）とグローバルLVとの間のRd係数。
  * `corx2t` : X変数とグローバルLVとの相関。

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
ytrain = y[s]
Xbltest = mblock(rmrow(X, s), listbl)
ytest = rmrow(y, s) 
ntrain = nro(ytrain) 
ntest = nro(ytest) 
ntot = ntrain + ntest 
(ntot = ntot, ntrain , ntest)

nlv = 3
bscal = :frob
model = mbplsr(; nlv, bscal)
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

## このMBPLSRは関数pipを使っても実装できます

model1 = blockscal(; bscal, centr = true) ;
model2 = mbconcat()
model3 = plskern(; nlv, scal = false) ;
model = pip(model1, model2, model3)
fit!(model, Xbltrain, ytrain)
@head T =  model.model[3].fitm.T  # = transf(model, Xbltrain)
transf(model, Xbltest)
predict(model, Xbltest).pred 
```
