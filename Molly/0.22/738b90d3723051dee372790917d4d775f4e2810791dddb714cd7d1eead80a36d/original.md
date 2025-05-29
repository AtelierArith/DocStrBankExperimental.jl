```
FENEBond(; k, r0, σ, ϵ)
```

A finitely extensible non-linear elastic (FENE) bond between two atoms, see [Kremer and Grest 1990](https://doi.org/10.1063/1.458541).

The potential energy is defined as

$$
V(r) = -\frac{1}{2} k r^2_0 \ln \left( 1 - \left( \frac{r}{r_0} \right) ^2 \right) + V_{\text{WCA}}(r)
$$

where the WCA contribution is given by

$$
V_{\text{WCA}}(r) =
    \begin{cases}
      4\varepsilon \left[ \left( \frac{\sigma}{r} \right) ^{12} - \left( \frac{\sigma}{r} \right) ^6 \right] + \varepsilon & r < 2^{1/6}\sigma\\
      0 & r \geq 2^{1/6}\sigma\\
    \end{cases}
$$
