```
LennardJonesSoftCore(; cutoff, α, λ, p, use_neighbors, shortcut, σ_mixing, ϵ_mixing,
                     weight_special)
```

ソフトコアを持つ2つの原子間のLennard-Jones 6-12相互作用。

ポテンシャルエネルギーは次のように定義されます。

$$
V(r_{ij}) = 4\varepsilon_{ij} \left[\left(\frac{\sigma_{ij}}{r_{ij}^{\text{sc}}}\right)^{12} - \left(\frac{\sigma_{ij}}{r_{ij}^{\text{sc}}}\right)^{6}\right]
$$

および各原子に対する力は次のように表されます。

$$
\vec{F}_i = 24\varepsilon_{ij} \left(2\frac{\sigma_{ij}^{12}}{(r_{ij}^{\text{sc}})^{13}} - \frac{\sigma_{ij}^6}{(r_{ij}^{\text{sc}})^{7}}\right) \left(\frac{r_{ij}}{r_{ij}^{\text{sc}}}\right)^5 \frac{\vec{r}_{ij}}{r_{ij}}
$$

ここで、

$$
r_{ij}^{\text{sc}} = \left(r_{ij}^6 + \alpha \sigma_{ij}^6 \lambda^p \right)^{1/6}
$$

もし$\alpha$または$\lambda$がゼロであれば、これは標準の[`LennardJones`](@ref)ポテンシャルを与えます。
