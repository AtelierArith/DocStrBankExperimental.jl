```
mlr(; kwargs...)
mlr(X, Y; kwargs...)
mlr(X, Y, weights::Weight; kwargs...)
mlr!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

QRアルゴリズムを使用して多重線形回帰モデル（MLR）を計算します。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。    `Weight`型でなければなりません（例えば、関数 `mweight` を参照）。

キーワード引数：

  * `noint` : ブール値。モデルが切片ありで計算されるかどうかを定義します。

安全ですが、他の方法よりも少し遅くなる可能性があります。

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie 
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2") 
@load db dat
@names dat
@head dat.X
X = dat.X[:, 2:4]
y = dat.X[:, 1]
n = nro(X)
ntest = 30
s = samprand(n, ntest) 
Xtrain = X[s.train, :]
ytrain = y[s.train]
Xtest = X[s.test, :]
ytest = y[s.test]

model = mlr()
#model = mlrchol()
#model = mlrpinv()
#model = mlrpinvn() 
fit!(model, Xtrain, ytrain) 
@names model
@names model.fitm
fitm = model.fitm ;
fitm.B
fitm.int 
coef(model) 
res = predict(model, Xtest)
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction",  
    ylabel = "Observed").f    

model = mlr(noint = true)
fit!(model, Xtrain, ytrain) 
coef(model) 

model = mlrvec()
fit!(model, Xtrain[:, 1], ytrain) 
coef(model) 
```
