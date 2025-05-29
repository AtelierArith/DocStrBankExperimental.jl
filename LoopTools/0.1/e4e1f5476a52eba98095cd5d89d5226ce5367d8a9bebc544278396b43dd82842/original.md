```
B0i(id, p^2, m1^2, m2^2)
```

two-point tensor coefficient for `id`

$$
\frac{μ^{4-D}}{iπ^{D/2} r_Γ} \int
\frac{({\rm numerator})\, d^D q }{(q^2-m_1^2)\left[(q+p)^2-m_2^2\right]}
$$

with $r_Γ = \frac{Γ^2(1-ε)Γ(1+ε)}{Γ(1-2ε)}$, $D=4-2ε$.

Special cases:

| `id`               |     Int     | Description                                        |
|:------------------ |:-----------:|:-------------------------------------------------- |
| `bb0`   (`dbb0`)   | `1` (`19`)  | (derivative of) scalar two-point one-loop function |
| `bb1`   (`dbb1`)   | `4` (`22`)  | (derivative of) coefficient of $p_{μ}$             |
| `bb00`  (`dbb00`)  | `7` (`25`)  | (derivative of) coefficient of $g_{μν}$            |
| `bb11`  (`dbb11`)  | `10` (`28`) | (derivative of) coefficient of $p_μ p_ν$           |
| `bb001` (`dbb001`) | `13` (`31`) | (derivative of) coefficient of $g_{μν}p_ρ$         |
| `bb111`            |    `16`     | coefficient of $p_μ p_ν p_ρ$                       |

Functions `B0`, `B1`, `B00`, `B11`, `B001` and `B111` are defined.
