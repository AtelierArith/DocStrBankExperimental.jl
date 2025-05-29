```
DensityDiffusionAntuono(initial_condition; delta)
```

[Antuono (2010)](@cite Antuono2010)によって一般的に使用される密度拡散項、いわゆるδ-SPH。 [Molteni (2009)](@cite Molteni2009)による密度拡散項は、[Antuono (2012)](@cite Antuono2012)によってうまく書き下ろされた第二項によって拡張されています。

[`DensityDiffusion`](@ref)の連続方程式における項$\psi_{ab}$は次のように定義されます。

$$
\psi_{ab} = 2\left(\rho_a - \rho_b - \frac{1}{2}\big(\nabla\rho^L_a + \nabla\rho^L_b\big) \cdot r_{ab}\right)
    \frac{r_{ab}}{\Vert r_{ab} \Vert^2},
$$

ここで、$\rho_a$と$\rho_b$はそれぞれ粒子$a$と$b$の密度を示し、$r_{ab} = r_a - r_b$は粒子$a$と$b$の座標の差です。記号$\nabla\rho^L_a$は、次のように定義される正規化された密度勾配を示します。

$$
\nabla\rho^L_a = -\sum_b (\rho_a - \rho_b) V_b L_a \nabla_{r_a} W(\Vert r_{ab} \Vert, h)
$$

ここで、

$$
L_a := \left( -\sum_{b} V_b r_{ab} \otimes \nabla_{r_a} W(\Vert r_{ab} \Vert, h) \right)^{-1} \in \R^{d \times d},
$$

$$
d
$$

は次元の数です。

実装された密度拡散項の概要と比較については、[`DensityDiffusion`](@ref)を参照してください。
