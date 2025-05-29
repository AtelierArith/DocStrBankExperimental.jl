```
acousticstiffness(self::FEMMAcoust, assembler::A, geom::NodalField, P::NodalField{T}) where {T<:Number, A<:AbstractSysmatAssembler}
```

音響の「剛性」行列を計算します。

# 引数

  * `self`   =  音響モデル
  * `assembler`  =  行列アセンブラ
  * `geom` = 幾何学フィールド
  * `P` = 音響（摂動）圧力フィールド

行列を返します。

音響の「剛性」行列は慣例的に剛性と呼ばれますが、その機械的意味はかなり異なります。（それは運動エネルギーに関係しています。）これは、音響圧力のためのこの行列ODEシステムにおける行列 $\mathbf{K}_a$ です：

$$
\mathbf{M}_a \mathbf{\ddot{p}}
+ \mathbf{K}_a \mathbf{{p}} =
\mathbf{{f}}
$$

!!! 注     行列を計算するために `FinEtools.FEMMBaseModule` の双線形形式関数 `bilform_diffusion` が使用されます。
