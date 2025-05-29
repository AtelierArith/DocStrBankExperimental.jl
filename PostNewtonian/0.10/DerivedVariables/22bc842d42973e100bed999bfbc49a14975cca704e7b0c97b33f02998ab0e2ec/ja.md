```
S⃗₀⁻(s)
S⃗₀⁻(M₁, M₂, κ₁, κ₂, S⃗₁, S⃗₂)
```

以下の式 (3.4) に定義されています [Buonanno et al. (2012)](https://arxiv.org/abs/1209.6349):

$$
\vec{S}_0^-
= \frac{M}{M_1} \left( \frac{\kappa_1} {\kappa_2} \right)^{1/4}
  \left( 1 - \sqrt{1 - \kappa_1 \kappa_2} \right)^{1/2} \vec{S}_1
  + \frac{M}{M_2} \left( \frac{\kappa_2} {\kappa_1} \right)^{1/4}
    \left( 1 + \sqrt{1 - \kappa_1 \kappa_2} \right)^{1/2} \vec{S}_2.
$$

現在、$\kappa_1$ と $\kappa_2$ はどちらも 1 と仮定されています。これはブラックホールの場合と同様です。自分の `PNSystem` タイプに対して他の値を持つように `κ₁` と `κ₂` を定義することができ、この関数は適切に動作します。

[`S⃗₀⁺`](@ref) も参照してください。
