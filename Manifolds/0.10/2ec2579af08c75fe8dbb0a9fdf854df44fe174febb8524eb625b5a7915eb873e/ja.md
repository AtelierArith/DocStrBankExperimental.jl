```
exp(M::Segre{ℝ, V}, p, X)
```

セグレ多様体上の指数写像。

$$
p ≐ (λ, x_1, …, x_d) ∈ \mathcal{S}
$$

および $X = (ν, u_1, …, u_d) ∈ T_p \mathcal{S}$ とします。指数写像は次のように与えられます。

$$
    \operatorname{exp}_p(X) ≐
    \left(
        \sqrt{(λ + ν)^2 + (λ m)^2},\\
        x_1 \cos\mathopen{\Big(} \frac{f \lVert u_1 \rVert_{x_1}}{m} \mathclose{\Big)} + \frac{u_1}{\lVert u_1 \rVert_{x_1}} \sin\mathopen{\Big(} \frac{f \lVert u_1 \rVert_{x_1}}{m} \mathclose{\Big)},\\
        …,\\
        x_d \cos\mathopen{\Big(} \frac{f \lVert u_d \rVert_{x_d}}{m} \mathclose{\Big)} + \frac{u_d}{\lVert u_d \rVert_{x_d}} \sin\mathopen{\Big(} \frac{f \lVert u_d \rVert_{x_d}}{m} \mathclose{\Big)}
    \right),
$$

ここで

$$
    \begin{aligned}
        f &= \frac{\pi}{2} - \tan^{-1}\mathopen{\Big(} \frac{λ + ν}{λ m} \mathclose{\Big)},\\
        m &= \sqrt{\lVert u_1 \rVert_{x_1}^2 + … + \lVert u_d \rVert_{x_d}^2}.
    \end{aligned}
$$

もし $m = 0$ かつ $-λ < ν$ であれば、$\operatorname{exp}_p(v) = p + X$ となります。

この公式は [JacobssonSwijsenVandervekenVannieuwenhoven:2024](@cite) の命題 3.1 で導出されています。
