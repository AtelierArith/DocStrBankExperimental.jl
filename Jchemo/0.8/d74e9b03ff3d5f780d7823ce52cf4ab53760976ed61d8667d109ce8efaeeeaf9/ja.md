```
sep(pred, Y)
```

修正されたSEP（"SEP_c"）を計算します。すなわち、予測誤差の標準偏差です。

  * `pred` : 予測値。
  * `Y` : 観測データ。

## 参考文献

Bellon-Maurel, V., Fernandez-Ahumada, E., Palagos, B.,  Roger, J.-M., McBratney, A., 2010. NIR分光法による土壌属性の予測の質を評価するために一般的に使用される化学計測指標の批判的レビュー。TrAC Trends in Analytical Chemistry 29,  1073–1081.  https://doi.org/10.1016/j.trac.2010.05.006

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
sep(pred, Ytest)

model = plskern(nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
sep(pred, ytest)
```
