```
pressure2resultanttorque(self::FEMMAcoustSurf, assembler::A,
  geom::NodalField,
  P::NodalField{T},
  Torque::GeneralField, CG::FFltVec) where {T<:Number, A<:AbstractSysmatAssembler}
```

与えられた圧力を表面上の結果トルクに変換する矩形結合行列を計算します。これはCGに関して表面に作用します。

# 引数

  * `self`   =  音響モデル
  * `assembler`  =  行列アセンブラ; 非対称行列を組み立てることができる必要があります
  * `geom` = 幾何学フィールド
  * `P` = 音響（摂動）圧力フィールド
  * `Torque` = トルク結果のためのフィールド
