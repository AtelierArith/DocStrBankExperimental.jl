```
C0i(id, p1^2, p2^2, (p1+p2)^2, m1^2, m2^2, m3^2)
```

three-point tensor coefficient for `id`

$$
\frac{μ^{4-D}}{iπ^{D/2} r_Γ} \int
\frac{({\rm numerator})\, d^D q }{(q^2-m_1^2)\left[(q+p_1)^2-m_2^2\right]
\left[(q+p_1+p_2)^2-m_3^2\right]}
$$

with $r_Γ = \frac{Γ^2(1-ε)Γ(1+ε)}{Γ(1-2ε)}$, $D=4-2ε$.

Special cases:

| `id`     |  Int  | Description                                  |
|:-------- |:-----:|:-------------------------------------------- |
| `cc0`    |  `1`  | scalar three-point one-loop function         |
| `cc1`    |  `4`  | coefficient of $k_{1μ}$                      |
| `cc2`    |  `7`  | coefficient of $k_{2μ}$                      |
| `cc00`   | `10`  | coefficient of $g_{μν}$                      |
| `cc11`   | `13`  | coefficient of $k_{1μ} k_{1ν}$               |
| `cc12`   | `16`  | coefficient of $k_{1μ} k_{2ν}$               |
| `cc22`   | `19`  | coefficient of $k_{2μ} k_{2ν}$               |
| `...`    | `...` | `...`                                        |
| `cc2222` | `64`  | coefficient of $k_{2μ} k_{2ν} k_{2ρ} k_{2σ}$ |

where $k_{1,2}$ are related to $p_{1,2}$ by  $k_{j} = \sum_{i=1}^j p_i$.
