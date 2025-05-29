```
struct NoChargeTrappingModel{T <: SSDFloat} <: AbstractChargeTrappingModel{T}
```

電荷がドリフト中に捕らえられない電荷捕獲モデルです。

このモデルは、設定ファイルに電荷捕獲モデルが定義されていない場合のデフォルトです。
