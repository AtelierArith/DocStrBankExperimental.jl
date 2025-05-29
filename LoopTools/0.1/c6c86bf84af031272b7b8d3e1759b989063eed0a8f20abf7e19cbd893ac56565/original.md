```
A0i(id, m^2)
```

one-point tensor coefficient for `id`

$$
\frac{μ^{4-D}}{iπ^{D/2} r_Γ} \int d^D q \frac{\{1, g_{μν} \} }{q^2-m^2}
$$

with $r_Γ = \frac{Γ^2(1-ε)Γ(1+ε)}{Γ(1-2ε)}$, $D=4-2ε$`.

Special cases:

| `id`   | Int | Description                                         |
|:------ |:---:|:--------------------------------------------------- |
| `aa0`  | `1` | scalar one-point one-loop function, i.e., `A0(m^2)` |
| `aa00` | `4` | coefficient of $g_{μν}$                             |
