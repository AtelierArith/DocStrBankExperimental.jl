```
uniaxial_increment!(material::AbstractMaterial, dstrain11::Real, dt::Real;
                    dstrain::AbstractVector{<:Real}=[dstrain11, -0.3*dstrain11, -0.3*dstrain11, 0.0, 0.0, 0.0],
                    max_iter::Integer=50, norm_acc::Real=1e-9)
```

`material`に対して互換性のあるひずみ増分を見つけます。

材料状態（`material.variables`）と*ひずみ*増分の成分11は指定された通りに取られます。

便利な関数; `general_increment!`を参照してください。

`find_dstrain!`を参照してください。
