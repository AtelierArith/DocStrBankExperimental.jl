```
ReplicatedSample(Z::AbstractVector)
```

This type represents `K` iid samples $Z_{i1},\dotsc, Z_{iK}$ drawn from the same distribution $F_i$. In the setting, for which Aurora was developed, the distribution $F_i$`is parameterized by its mean``\mu_i``, i.e.,

$$
\mu_i = \mathbb E_{F_i}[ Z_{ij}],
$$

as well as a nuisance parameter $lpha_i$, so that $F_i = F(\cdot \mid \mu_i, \alpha_i)$ and

$$
Z_{i1},\dotsc, Z_{iK} \mid  \mid \mu_i, \alpha_i \; \sim \; F(\cdot \mid \mu_i, \alpha_i).
$$
