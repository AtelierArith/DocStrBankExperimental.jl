```
S⃗₀⁻(s)
S⃗₀⁻(M₁, M₂, κ₁, κ₂, S⃗₁, S⃗₂)
```

Defined below Eq. (3.4) of [Buonanno et al. (2012)](https://arxiv.org/abs/1209.6349):

$$
\vec{S}_0^-
= \frac{M}{M_1} \left( \frac{\kappa_1} {\kappa_2} \right)^{1/4}
  \left( 1 - \sqrt{1 - \kappa_1 \kappa_2} \right)^{1/2} \vec{S}_1
  + \frac{M}{M_2} \left( \frac{\kappa_2} {\kappa_1} \right)^{1/4}
    \left( 1 + \sqrt{1 - \kappa_1 \kappa_2} \right)^{1/2} \vec{S}_2.
$$

Note that, currently, $\kappa_1$ and $\kappa_2$ are both assumed to be equal to 1, as is the case for black holes.  You can define `κ₁` and `κ₂` to have other values for your own `PNSystem` types, and this function will work appropriately.

See also [`S⃗₀⁺`](@ref).
