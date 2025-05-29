```
fitted(MLMNet::Mlmnet, lambda::Float64, alpha::Float64)
```

Mlmnetオブジェクトのフィッティング値を計算します。lambdaが与えられた場合 

# 引数

  * MLMNet = Mlmnetオブジェクト
  * lambda = 使用するラムダペナルティ、浮動小数点スカラー
  * alpha = L1とL2のペナルティの混合を決定するためのアルファペナルティ、浮動小数点スカラー

# 値

フィッティング値の2次元配列
