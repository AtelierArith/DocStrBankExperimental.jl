```
acousticmass(self::FEMMAcoust, assembler::A,
  geom::NodalField,
  Pddot::NodalField{T}) where {T<:Number,
  A<:AbstractSysmatAssembler}
```

音響質量行列を計算します。

# 引数

  * `self`   =  音響モデル
  * `assembler`  =  行列アセンブラ
  * `geom` = 幾何学フィールド
  * `Pddot` = 音響（摂動）圧力場の二次の変化率

音響の「質量」行列は慣例的に質量と呼ばれますが、その機械的意味はかなり異なります。（それはポテンシャルエネルギーに関係しています。）これは音響圧力のためのこの行列ODEシステムにおける行列 $\mathbf{M}_a$ です：

$$
\mathbf{M}_a \mathbf{\ddot{p}}
+ \mathbf{K}_a \mathbf{{p}} =
\mathbf{{f}}
$$

!!! 注     行列を計算するために `FinEtools.FEMMBaseModule` の双線形形式関数 `bilform_dot` が使用されます。
