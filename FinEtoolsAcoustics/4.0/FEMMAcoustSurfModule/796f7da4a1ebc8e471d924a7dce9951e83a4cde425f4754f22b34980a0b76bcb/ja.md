```
acousticrobin(
    self::FEMMAcoustSurf,
    assembler::A,
    geom::NodalField,
    Pdot::NodalField{T},
    impedance
) where {T<:Number,A<:AbstractSysmatAssembler}
```

音響「ロビン境界条件」（ダンピング）行列を計算します。

# 引数

  * `self`   =  音響モデル
  * `assembler`  =  行列アセンブラ; 非対称行列を組み立てることができる必要があります
  * `geom` = 幾何学フィールド
  * `Pdot` = 音響（摂動）圧力場のレート
  * `impedance` = 境界の音響インピーダンス

ここでは、この境界のインピーダンスが $ho c$ であると仮定します。
