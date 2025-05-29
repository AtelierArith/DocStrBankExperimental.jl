```
D0i(id, p1^2, p2^2, p3^2, p4^2, (p1+p2)^2, (p2+p3)^2, m1^2, m2^2, m3^2, m4^2)
```

four-point tensor coefficient for `id`

$$
\frac{μ^{4-D}}{iπ^{D/2} r_Γ} \int
\frac{({\rm numerator})\, d^D q }{(q^2-m_1^2)\left[(q+p_1)^2-m_2^2\right]
\left[(q+p_1+p_2)^2-m_3^2\right] \left[(q+p_1+p_2+p_3)^2-m_4^2\right]}
$$

with $r_Γ = \frac{Γ^2(1-ε)Γ(1+ε)}{Γ(1-2ε)}$, $D=4-2ε$.

Special cases:

| `id`      |  Int  | Description                                         |
|:--------- |:-----:|:--------------------------------------------------- |
| `dd0`     |  `1`  | scalar four-point one-loop function                 |
| `dd1`     |  `4`  | coefficient of $k_{1μ}$                             |
| `dd2`     |  `7`  | coefficient of $k_{2μ}$                             |
| `dd3`     | `10`  | coefficient of $k_{3μ}$                             |
| `dd00`    | `13`  | coefficient of $g_{μν}$                             |
| `...`     | `...` | `...`                                               |
| `dd33333` | `238` | coefficient of $k_{3μ} k_{3ν} k_{3ρ} k_{3σ} k_{3λ}$ |

where $k_{1,2,3}$ are related to the external momenta $p_{1,2,3}$ by  $k_{j} = \sum_{i=1}^j p_i$.
