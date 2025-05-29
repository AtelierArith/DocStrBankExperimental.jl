```
ssr(pred, Y)
```

予測誤差の二乗和 (SSR) を計算します。

  * `pred` : 予測値。
  * `Y` : 観測データ。

## 例

```julia
using Jchemo

Xtrain = rand(10, 5) 
Ytrain = rand(10, 2)
ytrain = Ytrain[:, 1]
Xtest = rand(4, 5) 
Ytest = rand(4, 2)
ytest = Ytest[:, 1]

model = plskern(nlv = 2)
fit!(model, Xtrain, Ytrain)
pred = predict(model, Xtest).pred
ssr(pred, Ytest)

model = plskern(nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
ssr(pred, ytest)
```
