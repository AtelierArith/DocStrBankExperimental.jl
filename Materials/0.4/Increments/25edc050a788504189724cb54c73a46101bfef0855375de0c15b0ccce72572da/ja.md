```
stress_driven_uniaxial_increment!(material::AbstractMaterial, dstress11::Real, dt::Real;
                                  dstrain::AbstractVector{<:Real}=[dstress11/200e3, -0.3*dstress11/200e3, -0.3*dstress11/200e3, 0.0, 0.0, 0.0],
                                  max_iter::Integer=50, norm_acc::Real=1e-9)
```

`material`に対して互換性のあるひずみ増分を見つけます。

材料状態（`material.variables`）と*応力*増分の成分11は指定されたものとして取られます。

便利な関数; `stress_driven_general_increment!`を参照してください。

`find_dstrain!`を参照してください。
