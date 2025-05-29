```
pcasvd(; kwargs...)
pcasvd(X; kwargs...)
pcasvd(X, weights::Weight; kwargs...)
pcasvd!(X::Matrix, weights::Weight; kwargs...)
```

SVD因子分解によるPCA。

  * `X` : Xデータ (n, p)。
  * `weights` : 観測値の重み (n)。    `Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 主成分 (PC) の数。
  * `scal` : ブール値。`true`の場合、`X`の各列はその未修正の標準偏差でスケーリングされます。

Dを重みの対角行列 (weights.w) とし、XをDのメトリックで中心化された行列とします。この関数は、メトリックDにおいて||X - T * V'||^2を最小化し、sqrt(D) * XのSVD因子分解を計算します：

  * sqrt(D) * X ~ U * S * V'

出力は次のとおりです：

  * `T` = D^(-1/2) * U * S
  * `V` = V
  * Sの対角成分

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie 
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2") 
@load db dat
@names dat
@head dat.X
X = dat.X[:, 1:4]
n = nro(X)
ntest = 30
s = samprand(n, ntest) 
@head Xtrain = X[s.train, :]
@head Xtest = X[s.test, :]

nlv = 3
model = pcasvd(; nlv)
#model = pcaeigen(; nlv)
#model = pcaeigenk(; nlv)
#model = pcanipals(; nlv)
fit!(model, Xtrain)
@names model
@names model.fitm
@head T = model.fitm.T
## 同じ：
@head transf(model, X)
T' * T
@head V = model.fitm.V
V' * V

@head Ttest = transf(model, Xtest)

res = summary(model, Xtrain) ;
@names res
res.explvarx
res.contr_var
res.coord_var
res.cor_circle
```
