```
soplsr(; kwargs...)
soplsr(Xbl, Y; kwargs...)
soplsr(Xbl, Y, weights::Weight; kwargs...)
soplsr!(Xbl::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

マルチブロック逐次直交化PLSR（SO-PLSR）。

  * `Xbl` : Xデータのブロックのリスト（行列のベクトル）    通常、（n, p）データの関数`mblock`の出力。
  * `Y` : Yデータ（n, q）。
  * `weights` : 観測値の重み（n）。    `Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数（LVs = スコア）の数。
  * `scal` : ブール値。`true`の場合、`Xbl`および`Y`のブロックの各列は、その未修正の標準偏差でスケーリングされます。

## 参考文献

Biancolillo et al. , 2015. SO-PLSと線形判別分析を組み合わせたマルチブロック分類。  Chemometrics and Intelligent Laboratory Systems, 141, 58-67.

Biancolillo, A. 2016. 食品分析に焦点を当てたマルチブロック分析の分野における方法開発。博士号。 コペンハーゲン大学。

Menichelli et al., 2014. パスモデリングのための探索ツールとしてのSO-PLS。 食品の品質と嗜好、36, 122-134。

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

nlv = 2
#nlv = [2, 1, 2]
#nlv = [2, 0, 1]
scal = false
#scal = true
model = soplsr(; nlv, scal)
fit!(model, Xbltrain, ytrain)
@names model 
@names model.fitm
@head model.fitm.T
@head transf(model, Xbltrain)
transf(model, Xbltest)

res = predict(model, Xbltest)
res.pred 
rmsep(res.pred, ytest)
```
