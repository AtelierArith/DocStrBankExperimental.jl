```
errp(pred, y)
```

分類誤差率 (ERRP) を計算します。

  * `pred` : 予測値。
  * `y` : 観測データ (クラスメンバーシップ)。

## 例

```julia
using Jchemo

Xtrain = rand(10, 5) 
ytrain = rand(["a" ; "b"], 10)
Xtest = rand(4, 5) 
ytest = rand(["a" ; "b"], 4)

model = plsrda(; nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
errp(pred, ytest)
```
