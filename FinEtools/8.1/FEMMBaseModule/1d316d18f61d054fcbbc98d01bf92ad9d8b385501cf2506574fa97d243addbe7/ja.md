```
bilform_lin_elastic(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    u::NodalField{T},
    cf::DC
) where {FEMM<:AbstractFEMM, A<:AbstractSysmatAssembler, FT, T, DC<:DataCache}
```

線形弾性型の双線形形式によって示されるスパース行列を計算します。

$$
\int_{V} (B \mathbf{w})^T C  B \mathbf{u}   \; \mathrm{d} V
$$

ここで、$\mathbf{w}$はベクトルテスト関数、$\mathbf{u}$は変位（速度）、$C$は弾性（粘性）行列です。$C$は与えられた関数`cf`によって計算されます（データ）。テスト関数と試行関数は同じ近似空間からのものであると仮定されています。`cf`は[`DataCache`](@ref)で表され、適切なサイズの行列を返す必要があります。

積分は領域$V$の体積に関して行われます（すなわち、三次元積分です）。

# 引数

  * `self` = 有限要素マシン;
  * `assembler` = グローバル行列のアセンブラ;
  * `geom` = 幾何学フィールド;
  * `u` = 速度フィールド;
  * `viscf`= データキャッシュで、積分点の位置、ヤコビ行列、および有限要素ラベルが与えられたときに係数$\mu$を評価するために呼び出されます。
