```
ev_integrate(
        self::FEMM,
        geom::NodalField{FT},
        f::DC,
        initial::R,
        m,
) where {FEMM<:AbstractFEMM, FT<:Number, DC<:DataCache, R}
```

与えられた関数のメッシュ領域上の積分を計算します。

$$
\int_{\Omega}  {f} \; \mathrm{d} \Omega
$$

ここで ${f}$ は与えられた関数（データ）です。データ ${f}$ は [`DataCache`](@ref) で表されます。

# 引数

  * `self` = 有限要素マシン;
  * `geom` = 幾何学的フィールド;
  * `f`= データキャッシュで、位置、ヤコビ行列、有限要素識別子、および数値点に基づいて被積分関数を評価するために呼び出されます;
  * `initial` = 積分の初期値,
  * `m`= 多様体の次元、0= 頂点（点）、1= 曲線、2= 表面、3= 体積。体荷の場合、`m` は3に設定され、表面の引張力の場合は2に設定されます。
