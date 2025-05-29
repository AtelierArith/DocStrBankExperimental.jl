```
FENEBond(; k, r0, σ, ϵ)
```

2つの原子間の有限伸長非線形弾性（FENE）ボンド、詳細は[Kremer and Grest 1990](https://doi.org/10.1063/1.458541)を参照してください。

ポテンシャルエネルギーは次のように定義されます。

$$
V(r) = -\frac{1}{2} k r^2_0 \ln \left( 1 - \left( \frac{r}{r_0} \right) ^2 \right) + V_{\text{WCA}}(r)
$$

ここで、WCAの寄与は次のように与えられます。

$$
V_{\text{WCA}}(r) =
    \begin{cases}
      4\varepsilon \left[ \left( \frac{\sigma}{r} \right) ^{12} - \left( \frac{\sigma}{r} \right) ^6 \right] + \varepsilon & r < 2^{1/6}\sigma\\
      0 & r \geq 2^{1/6}\sigma\\
    \end{cases}
$$
