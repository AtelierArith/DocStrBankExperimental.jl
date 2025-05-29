```
merrp(pred, y)
```

クラス内分類誤差率の平均を計算します。

  * `pred` : 予測値。
  * `y` : 観測データ（クラスメンバーシップ）。

ERRP（関数 `errp` を参照）は各クラスについて計算されます。関数 `merrp` はこれらのクラス内 ERRP の平均を返します。   

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
merrp(pred, ytest)
```
