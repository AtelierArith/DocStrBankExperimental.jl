```
resid(MLMNet::Mlmnet, lambda::Float64, alpha::Float64, newData::RawData=MLMNet.data)
```

MLMNetオブジェクトの残差を計算します。与えられたlambdaに基づいて

# 引数

  * MLMNet = Mlmnetオブジェクト
  * lambda = 使用するlambdaペナルティ、浮動小数点スカラー
  * alpha = L1とL2のペナルティの混合を決定するためのalphaペナルティ、浮動小数点スカラー
  * newData = RawDataオブジェクト。デフォルトでは、モデルをフィットさせるために使用されたMLMオブジェクトのデータフィールドになります。

# 値

残差の2次元配列
