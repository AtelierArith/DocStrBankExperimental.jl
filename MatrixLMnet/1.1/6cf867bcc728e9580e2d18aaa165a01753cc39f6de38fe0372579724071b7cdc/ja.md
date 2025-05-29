```
predict(MLMNet::Mlmnet, lambda::Float64, alpha::Float64,
             newPredictors::Predictors=MLMNet.data.predictors)
```

Mlmnetオブジェクトに基づいて新しい予測を計算し、指定されたlambdaを使用します。

# 引数

  * MLMNet = Mlmnetオブジェクト
  * lambda = 使用するペナルティのlambda、浮動小数点スカラー
  * alpha = L1とL2のペナルティの混合を決定するためのalphaペナルティ、浮動小数点スカラー
  * newPredictors = Predictorsオブジェクト。デフォルトでは、モデルをフィットさせるために使用されたMLMオブジェクトのdata.predictorsフィールドになります。

# 値

予測値の2次元配列
