```
DensityDiffusionFerrari()
```

[Ferrari (2009)](@cite Ferrari2009)による密度拡散項。

[`DensityDiffusion`](@ref)の連続の方程式における項$\psi_{ab}$は次のように定義されます。

$$
\psi_{ab} = \frac{\rho_a - \rho_b}{h_a + h_b} \frac{r_{ab}}{\Vert r_{ab} \Vert},
$$

ここで、$\rho_a$と$\rho_b$はそれぞれ粒子$a$と$b$の密度を示し、$r_{ab} = r_a - r_b$は粒子$a$と$b$の座標の差であり、$h_a$と$h_b$はそれぞれ粒子$a$と$b$のスムージング長です。

実装された密度拡散項の概要と比較については[`DensityDiffusion`](@ref)を参照してください。
