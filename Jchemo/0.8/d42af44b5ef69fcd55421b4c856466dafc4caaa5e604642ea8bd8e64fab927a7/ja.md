```
rpd(pred, Y)
```

モデル性能に対する偏差の比率（RPD）を計算します。

  * `pred` : 予測値。
  * `Y` : 観測データ。

これは、偏差に対するモデル性能の偏差の比率であり、次のように定義されます：

  * RPD = Std(Y) / RMSEP

ここで、Std(Y)は標準偏差です。

Std(Y) = RMSEP(null model) であり、null modelは単純平均であるため、これにより次のことも得られます：

  * RPD = RMSEP(null model) / RMSEP

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
rpd(pred, Ytest)

model = plskern(nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
rpd(pred, ytest)
```
