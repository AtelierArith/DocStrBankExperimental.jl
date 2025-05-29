```
linform_dot(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    P::NodalField{T},
    f::DC,
    m,
) where {FEMM<:AbstractFEMM, A<:AbstractSysvecAssembler, FT<:Number, T, DC<:DataCache}
```

線形形式「dot」によって示される離散ベクトルを計算します。

$$
\int_{V}  \mathbf{w} \cdot \mathbf{f} \; \mathrm{d} V
$$

ここで $\mathbf{w}$ はテスト関数、$\mathbf{f}$ は与えられた関数（データ）です。両方ともベクトルであると仮定されており、長さが1の場合でもスカラーを表します。データ $\mathbf{f}$ は [`DataCache`](@ref) で表されます。

# 引数

  * `self` = 有限要素マシン;
  * `assembler` = グローバルベクトルのアセンブラ;
  * `geom` = 幾何学的フィールド;
  * `P` = 自由度番号を定義するノードフィールド;
  * `f`= データキャッシュで、位置、ヤコビ行列、有限要素識別子、および数値点に基づいて被積分関数を評価するために呼び出されます;
  * `m`= 多様体の次元、0= 頂点（点）、1= 曲線、2= 表面、3= 体積。体荷の場合、`m` は3に設定され、表面の引張に対しては2に設定されます。
