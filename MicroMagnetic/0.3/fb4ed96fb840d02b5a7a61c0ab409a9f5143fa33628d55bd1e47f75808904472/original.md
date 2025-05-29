```
add_cubic_anis(sim::AbstractSim, Kc::Float64; axis1=(1,0,0), axis2=(0,1,0), name="cubic")
```

add a cubic anisotropy with default axis (1,0,0) , (0,1,0), and (0,0,1). The third axis is defined as axis3 = axis1 x axis2.

$$
  E_\mathrm{cubic} = -\int_{V} K_c (m_x^4 + m_y^4 + m_z^4) \, dV
$$

# Example

```julia
    add_cubic_anis(sim, 1e3, (1, 1, 0), (1, -1, 0))
```
