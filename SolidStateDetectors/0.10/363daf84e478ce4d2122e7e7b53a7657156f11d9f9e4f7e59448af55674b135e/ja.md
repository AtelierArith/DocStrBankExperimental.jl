```
struct ElectricFieldChargeDriftModel{T <: SSDFloat} <: AbstractChargeDriftModel{T}
```

電場に沿って電子とホールが± 1m²/Vsの移動度で漂流する電荷漂流モデルです。

このモデルは、設定ファイルに電荷漂流モデルが定義されていない場合のデフォルトです。
