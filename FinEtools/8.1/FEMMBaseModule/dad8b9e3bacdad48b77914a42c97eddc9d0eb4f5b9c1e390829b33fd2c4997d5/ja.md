```
bilform_div_grad(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    u::NodalField{T},
    viscf::DC
) where {FEMM<:AbstractFEMM, A<:AbstractSysmatAssembler, FT, T, DC<:DataCache}
```

「div grad」型の双線形形式によって示されるスパース行列を計算します。

$$
\int_{V}  \mu \nabla \mathbf{w}:  \nabla\mathbf{u}   \; \mathrm{d} V
$$

ここで、$\mathbf{w}$はベクトルテスト関数、$\mathbf{u}$は速度、$\mu$は動的粘度（または運動粘度、定式化に応じて）です。$\mu$は、与えられた関数（データ）である`viscf`によって計算されます。テスト関数と試行関数は同じ近似空間からのものであると仮定されています。`viscf`は[`DataCache`](@ref)で表され、スカラー粘度を返す必要があります。

積分は領域$V$の体積に関して行われます（すなわち、三次元積分です）。

# 引数

  * `self` = 有限要素マシン;
  * `assembler` = グローバル行列のアセンブラ;
  * `geom` = 幾何学的フィールド;
  * `u` = 速度フィールド;
  * `viscf`= データキャッシュで、積分点の位置、ヤコビ行列、および有限要素ラベルが与えられたときに係数$\mu$を評価するために呼び出されます。
