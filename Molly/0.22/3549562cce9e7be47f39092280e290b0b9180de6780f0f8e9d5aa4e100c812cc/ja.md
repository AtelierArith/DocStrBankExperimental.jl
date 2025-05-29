```
Yukawa(; cutoff, use_neighbors, weight_special, coulomb_const, kappa)
```

二つの原子間のユカワ静電相互作用。

ポテンシャルエネルギーは次のように定義されます。

$$
V(r_{ij}) = \frac{q_i q_j}{4 \pi \varepsilon_0 r_{ij}} \exp(-\kappa r_{ij})
$$

そして、各原子に対する力は次のようになります。

$$
F(r_{ij}) = \frac{q_i q_j}{4 \pi \varepsilon_0 r_{ij}^2} \exp(-\kappa r_{ij})\left(\kappa r_{ij} + 1\right) \vec{r}_{ij}
$$
