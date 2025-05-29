```
pressure2resultantforce(self::FEMMAcoustSurf, assembler::A,
  geom::NodalField,
  P::NodalField{T},
   Force::Field) where {T<:Number, A<:AbstractSysmatAssembler}
```

与えられた表面上の圧力を表面に作用する結果の力に変換する矩形結合行列を計算します。

# 引数

  * `self`   =  音響モデル
  * `assembler`  =  行列アセンブラ; 非対称行列を組み立てることができる必要があります
  * `geom` = 幾何学フィールド
  * `P` = 音響（摂動）圧力フィールド
  * `Force` = 力の結果のためのフィールド
