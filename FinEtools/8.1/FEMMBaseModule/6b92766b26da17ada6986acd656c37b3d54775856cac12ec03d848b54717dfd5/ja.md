```
bilform_dot(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    u::NodalField{T},
    cf::DC
) where {FEMM<:AbstractFEMM, A<:AbstractSysmatAssembler, FT, T, DC<:DataCache}
```

"ドット"型の双線形形式によって示されるスパース行列を計算します。

$$
\int_{\Omega}  \mathbf{w} \cdot \mathbf{c} \cdot \mathbf{u} \; \mathrm{d} \Omega
$$

ここで、$\mathbf{w}$はテスト関数、$\mathbf{u}$は試行関数、$\mathbf{c}$は係数の正方行列です。$\mathbf {c}$は与えられた関数（データ）である`cf`によって計算されます。試行関数とテスト関数はベクトルであると仮定されます（長さが1の場合でも）。`cf`は[`DataCache`](@ref)で表され、`u`フィールドのノードごとの自由度の数に等しい次元の正方行列を返す必要があります。

積分領域$\Omega$は、領域の体積$V$（すなわち三次元積分）、または表面$S$（すなわち二次元積分）、または線分領域$L$（すなわち一次元積分）である可能性があります。

# 引数

  * `self` = 有限要素マシン;
  * `assembler` = グローバルオブジェクトのアセンブラ;
  * `geom` = 幾何学フィールド;
  * `u` = 自由度番号を定義するノードフィールド;
  * `cf`= データキャッシュで、積分点の位置、ヤコビ行列、および有限要素ラベルが与えられたときに係数$c$を評価するために呼び出されます。
  * `m` = 多様体の次元（デフォルトは3）。
