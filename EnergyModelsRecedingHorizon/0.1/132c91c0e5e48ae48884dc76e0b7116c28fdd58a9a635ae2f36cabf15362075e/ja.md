```
struct StorageValueCut
```

`StorageValueCut`は、最適化のホライズンの終わりに保存されたリソースの値に上限を設定する切断ハイパープレーンを表します。

## フィールド

  * **`id::Any`** は `StorageValueCut` の名前/識別子です。
  * **`coeffs::Vector{<:ElementValue}`** は、指定された `Storage` ノードのレベルに関連付けられたカット係数です。これらは `Dict{<:Storage{<:Accumulating}, <:Real}` として提供することもできます。
  * **`rhs::Real`** はカットの右辺定数です。
