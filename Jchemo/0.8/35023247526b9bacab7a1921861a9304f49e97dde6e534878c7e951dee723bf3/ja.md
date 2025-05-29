```
rmsepstand(pred, Y)
```

予測誤差の二乗平均の標準化平方根を計算します (RMSEP_stand)。

  * `pred` : 予測値。
  * `Y` : 観測データ。

RMSEPは`Y`に標準化されます：

  * RMSEP_stand = RMSEP ./ `Y`。

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
rmsepstand(pred, Ytest)

model = plskern(nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
rmsepstand(pred, ytest)
```
