```julia
struct EstimationSetup{U<:MomentMatching.EstimationMode}
```

# 説明

モーメントマッチング推定手順のセットアップを保存するための構造体。

# フィールド

  * `mode`: 推定モード。
  * `modelname`: 推定のためのサブメソッド。どのパラメータがどのように推定されるかをエンコードした文字列。
  * `typemom`: 推定のためのサブメソッド。どのモーメントがターゲットにされるかをエンコードした文字列。
