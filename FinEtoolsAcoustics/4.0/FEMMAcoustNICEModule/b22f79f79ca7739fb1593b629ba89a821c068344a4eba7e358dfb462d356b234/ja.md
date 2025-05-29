```
acousticstiffness(self::FEMMAcoustNICE, assembler::A, geom::NodalField, P::NodalField{T}) where {T<:Number, A<:AbstractSysmatAssembler}
```

音響質量行列を計算します。

# 引数

  * `self`   =  音響モデル
  * `assembler`  =  行列アセンブラ
  * `geom` = 幾何学フィールド
  * `P` = 音響（摂動）圧力フィールド

行列を返します。
