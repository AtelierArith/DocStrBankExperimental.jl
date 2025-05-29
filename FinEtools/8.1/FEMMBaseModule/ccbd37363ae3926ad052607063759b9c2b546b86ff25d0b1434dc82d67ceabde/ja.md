```
bilform_convection(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    u::NodalField{T},
    Q::NodalField{QT},
    rhof::DC
) where {FEMM<:AbstractFEMM, A<:AbstractSysmatAssembler, FT, T, QT, DC<:DataCache}
```

対流型の双線形形式によって示されるスパース行列を計算します。

$$
\int_{V}  {w} \rho \mathbf{u} \cdot \nabla q \; \mathrm{d} V
$$

ここで $w$ はスカラー試験関数、$\mathbf{u}$ は対流速度、$q$ はスカラー試行関数、$\rho$ は質量密度です。$\rho$ は与えられた関数 `rhof` によって計算されます。試験関数と試行関数は同じ近似空間からのものであると仮定されています。`rhof` は [`DataCache`](@ref) で表され、スカラー質量密度を返す必要があります。

この積分は領域 $V$ の体積に関して行われます（すなわち、三次元積分です）。

# 引数

  * `self` = 有限要素マシン;
  * `assembler` = グローバル行列のアセンブラ;
  * `geom` = 幾何学的フィールド;
  * `u` = 対流速度フィールド;
  * `Q` = 自由度番号を定義するノードフィールド;
  * `rhof`= データキャッシュで、積分点の位置、ヤコビ行列、および有限要素ラベルが与えられたときに係数 $\rho$ を評価するために呼び出されます。
