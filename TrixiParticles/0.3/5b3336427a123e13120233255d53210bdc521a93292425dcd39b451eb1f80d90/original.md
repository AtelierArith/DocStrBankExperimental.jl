```
ContinuityDensity()
```

Density calculator to integrate the density from the continuity equation

$$
\frac{\mathrm{d}\rho_a}{\mathrm{d}t} = \sum_{b} m_b v_{ab} \cdot \nabla_{r_a} W(\Vert r_a - r_b \Vert, h),
$$

where $\rho_a$ denotes the density of particle $a$ and $r_{ab} = r_a - r_b$ is the difference of the coordinates, $v_{ab} = v_a - v_b$ of the velocities of particles $a$ and $b$.
