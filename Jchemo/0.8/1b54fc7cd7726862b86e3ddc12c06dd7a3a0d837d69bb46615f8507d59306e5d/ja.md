```
xfit(object)
xfit(object, X; nlv = nothing)
xfit!(object, X::Matrix; nlv = nothing)
```

双線形モデル（例：PCA）からの行列フィッティング。

  * `object` : フィッティングされたモデル。
  * `X` : モデルから近似される新しいXデータ。   モデル`object`をフィットさせるために使用されたXデータと同じスケールでなければなりません。すなわち、センタリングおよび最終的なスケーリングの前です。

キーワード引数：

  * `nlv` : 考慮すべき成分の数（PCまたはLV）。    `nothing`の場合、最大の成分数です。

双線形モデル（例：PCAまたはPLS）に基づいて行列`X`の近似を計算します。フィッティングされたXは、モデル`object`をフィットさせるために使用されたXデータの元のスケールで返されます。

## 例

```julia
using Jchemo

X = [1. 2 3 4; 4 1 6 7; 12 5 6 13; 
    27 18 7 6; 12 11 28 7] 
Y = [10. 11 13; 120 131 27; 8 12 4; 
    1 200 8; 100 10 89] 
n, p = size(X)
Xnew = X[1:3, :]
Ynew = Y[1:3, :]
y = Y[:, 1]
ynew = Ynew[:, 1]
weights = mweight(rand(n))

nlv = 2 
scal = false
#scal = true
model = pcasvd(; nlv, scal) ;
fit!(model, X)
fitm = model.fitm ;
@head xfit(fitm)
xfit(fitm, Xnew)
xfit(fitm, Xnew; nlv = 0)
xfit(fitm, Xnew; nlv = 1)
fitm.xmeans

@head X
@head xfit(fitm) + xresid(fitm, X)
@head xfit(fitm, X; nlv = 1) + xresid(fitm, X; nlv = 1)

@head Xnew
@head xfit(fitm, Xnew) + xresid(fitm, Xnew)

model = pcasvd(; nlv = min(n, p), scal) 
fit!(model, X)
fitm = model.fitm ;
@head xfit(fitm) 
@head xfit(fitm, X)
@head xresid(fitm, X)

nlv = 3
scal = false
#scal = true
model = plskern(; nlv, scal)
fit!(model, X, Y, weights) 
fitm = model.fitm ;
@head xfit(fitm)
xfit(fitm, Xnew)
xfit(fitm, Xnew, nlv = 0)
xfit(fitm, Xnew, nlv = 1)

@head X
@head xfit(fitm) + xresid(fitm, X)
@head xfit(fitm, X; nlv = 1) + xresid(fitm, X; nlv = 1)

@head Xnew
@head xfit(fitm, Xnew) + xresid(fitm, Xnew)

model = plskern(; nlv = min(n, p), scal) 
fit!(model, X, Y, weights) 
fitm = model.fitm ;
@head xfit(fitm) 
@head xfit(fitm, Xnew)
@head xresid(fitm, Xnew)
```
