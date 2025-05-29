```
r2(pred, Y)
```

R2係数を計算します。

  * `pred` : 予測値。
  * `Y` : 観測データ。

R2の率は次のように計算されます：

  * R2 = 1 - MSEP(現在のモデル) / MSEP(ヌルモデル)

ここで「ヌルモデル」とは全体の平均です。CVまたはテストセットに対する予測や、非線形モデルの場合、真のデータと予測値との相関係数の二乗（`cor2`）とは異なる場合があります。

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
r2(pred, Ytest)

model = plskern(nlv = 2)
fit!(model, Xtrain, ytrain)
pred = predict(model, Xtest).pred
r2(pred, ytest)
```
