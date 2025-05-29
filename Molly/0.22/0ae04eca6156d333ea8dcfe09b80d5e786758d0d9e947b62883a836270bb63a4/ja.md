```
CoulombSoftCore(; cutoff, α, λ, p, use_neighbors, σ_mixing, weight_special, coulomb_const)
```

ソフトコアを持つ二つの原子間のクーロン静電相互作用。

ポテンシャルエネルギーは次のように定義されます。

$$
V(r_{ij}) = \frac{q_i q_j}{4 \pi \varepsilon_0 (r_{ij}^6 + \alpha  \sigma_{ij}^6  \lambda^p)^{\frac{1}{6}}}
$$

もし$\alpha$または$\lambda$がゼロであれば、これは標準の[`Coulomb`](@ref)ポテンシャルを与えます。
