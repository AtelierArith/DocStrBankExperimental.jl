```
E0i(id, p1^2, p2^2, p3^2, p4^2, p5^2, (p1+p2)^2, (p2+p3)^2, (p3+p4)^2, (p4+p5)^2, 
(p5+p1)^2, m1^2, m2^2, m3^2, m4^2, m5^2)
```

five-point tensor coefficient for `id`

$$
\begin{aligned}
\frac{μ^{4-D}}{iπ^{D/2} r_Γ} \int d^D q &
\frac{({\rm numerator}) }{(q^2-m_1^2)\left[(q+p_1)^2-m_2^2\right]
\left[(q+p_1+p_2)^2-m_3^2\right] \left[(q+p_1+p_2+p_3)^2-m_4^2\right]} \\
&\times \frac1{\left[(q+p_1+p_2+p_3+p_4)^2-m_5^2\right]}
 \end{aligned}
$$

with $r_Γ = \frac{Γ^2(1-ε)Γ(1+ε)}{Γ(1-2ε)}$, $D=4-2ε$.

Special cases:

| `id`     |  Int  | Description                                  |
|:-------- |:-----:|:-------------------------------------------- |
| `ee0`    |  `1`  | scalar five-point one-loop function          |
| `ee1`    |  `4`  | coefficient of $k_{1μ}$                      |
| `ee2`    |  `7`  | coefficient of $k_{2μ}$                      |
| `ee3`    | `10`  | coefficient of $k_{3μ}$                      |
| `ee00`   | `13`  | coefficient of $g_{μν}$                      |
| `...`    | `...` | `...`                                        |
| `ee4444` | `256` | coefficient of $k_{4μ} k_{4ν} k_{4ρ} k_{4σ}$ |

where $k_{1,2,3,4}$ are related to the external momenta $p_{1,2,3,4}$ by  $k_{j} = \sum_{i=1}^j p_i$.
