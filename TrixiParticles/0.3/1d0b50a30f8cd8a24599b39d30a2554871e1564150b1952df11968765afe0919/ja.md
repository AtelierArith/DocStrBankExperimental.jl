```
DensityDiffusionMolteniColagrossi(; delta)
```

[Molteni (2009)](@cite Molteni2009)によって一般的に使用される密度拡散項。

[`DensityDiffusion`](@ref)の連続方程式における項$\psi_{ab}$は次のように定義されます。

$$
\psi_{ab} = 2(\rho_a - \rho_b) \frac{r_{ab}}{\Vert r_{ab} \Vert^2},
$$

ここで、$\rho_a$と$\rho_b$はそれぞれ粒子$a$と$b$の密度を示し、$r_{ab} = r_a - r_b$は粒子$a$と$b$の座標の差です。

実装された密度拡散項の概要と比較については[`DensityDiffusion`](@ref)を参照してください。
