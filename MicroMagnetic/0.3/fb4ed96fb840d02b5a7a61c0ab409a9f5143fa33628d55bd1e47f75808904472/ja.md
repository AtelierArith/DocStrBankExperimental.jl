```
add_cubic_anis(sim::AbstractSim, Kc::Float64; axis1=(1,0,0), axis2=(0,1,0), name="cubic")
```

デフォルトの軸 (1,0,0)、(0,1,0)、および (0,0,1) を持つ立方体異方性を追加します。第三の軸は axis3 = axis1 x axis2 と定義されます。

$$
  E_\mathrm{cubic} = -\int_{V} K_c (m_x^4 + m_y^4 + m_z^4) \, dV
$$

# 例

```julia
    add_cubic_anis(sim, 1e3, (1, 1, 0), (1, -1, 0))
```
