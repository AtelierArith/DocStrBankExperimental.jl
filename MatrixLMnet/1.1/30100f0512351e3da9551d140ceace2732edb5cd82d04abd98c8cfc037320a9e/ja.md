```
predict(MLMNet::Mlmnet, newPredictors::Predictors=MLMNet.data.predictors)
```

Mlmnetオブジェクトに基づいて新しい予測を計算します

# 引数

  * MLMNet = Mlmnetオブジェクト
  * newPredictors = Predictorsオブジェクト。モデルをフィットさせるために使用されたMLMオブジェクトのdata.predictorsフィールドがデフォルトです。

# 値

予測値の4次元配列
