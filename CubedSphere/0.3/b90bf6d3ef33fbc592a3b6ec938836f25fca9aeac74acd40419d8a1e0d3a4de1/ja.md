```
conformal_cubed_sphere_mapping(x, y; W_map=W_Rancic)
```

単位半径の球の同等のセクターに立方体の面からの準同型写像。

座標 $(x, y)$ を持つ立方体の北極面を、座標 $(X, Y, Z)$ を持つ球の同等のセクターに写像します。

立方体の面は $z$ 軸に対して法線方向に配置され、座標は $-1 ≤ x ≤ 1$、$-1 ≤ y ≤ 1$ の範囲内にあり、その中心は $(x, y) = (0, 0)$ にあります。座標 $X, Y$ は $x, y$ と同じ方向に増加します。

ここで使用される数値的な準同型写像は [Rancic-etal-1996](@citet) によって説明されています。

これは、Jim Purser と Misha Rančić による Fortran 77 コードに基づいた [MITgcm からの MATLAB コード](http://wwwcvs.mitgcm.org/viewvc/MITgcm/MITgcm_contrib/high_res_cube/matlab-grid-generator/map_xy2xyz.m?view=markup) の Julia 翻訳です。

# 例

立方体の面の中心 $(x, y) = (0, 0)$ は $(X, Y, Z) = (0, 0, 1)$ に写像されます。

```jldoctest
julia> using CubedSphere

julia> conformal_cubed_sphere_mapping(0, 0)
(0, 0, 1.0)
```

そして、立方体の面の端 $(x, y) = (1, 1)$ は $(X, Y, Z) = (√3/3, √3/3, √3/3)$ に写像されます。

```jldoctest
julia> using CubedSphere

julia> conformal_cubed_sphere_mapping(1, 1)
(0.5773502691896256, 0.5773502691896256, 0.5773502691896257)
```

# 参考文献

  * [Rancic-etal-1996](@cite) Rančić et al., *Q. J. R. Meteorol.*, (1996).
