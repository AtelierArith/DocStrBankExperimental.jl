```
coef(MLMNet::Mlmnet, lambda::Float64, alpha::Float64)
```

Mlmnetオブジェクトから指定されたlambdaで係数を抽出します。

# 引数

  * MLMNet = Mlmnetオブジェクト
  * lambda = 使用するlambdaペナルティ、浮動小数点スカラー
  * alpha = L1とL2のペナルティの混合を決定するためのalphaペナルティ、浮動小数点スカラー

# 値

係数の2次元配列
