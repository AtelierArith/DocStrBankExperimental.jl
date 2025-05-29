```
ContinuityDensity()
```

密度計算機は連続の方程式から密度を統合します

$$
\frac{\mathrm{d}\rho_a}{\mathrm{d}t} = \sum_{b} m_b v_{ab} \cdot \nabla_{r_a} W(\Vert r_a - r_b \Vert, h),
$$

ここで、$\rho_a$は粒子$a$の密度を示し、$r_{ab} = r_a - r_b$は座標の差、$v_{ab} = v_a - v_b$は粒子$a$と$b$の速度の差です。
