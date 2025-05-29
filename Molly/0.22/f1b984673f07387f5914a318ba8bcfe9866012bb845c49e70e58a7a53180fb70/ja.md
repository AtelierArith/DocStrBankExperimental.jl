```
Mie(; m, n, cutoff, use_neighbors, shortcut, σ_mixing, ϵ_mixing, weight_special)
```

2つの原子間のMie一般化相互作用。

`m`が6で`n`が12の場合、これはLennard-Jones相互作用に相当します。ポテンシャルエネルギーは次のように定義されます。

$$
V(r_{ij}) = C \varepsilon_{ij} \left[\left(\frac{\sigma_{ij}}{r_{ij}}\right)^n - \left(\frac{\sigma_{ij}}{r_{ij}}\right)^m\right]
$$

ここで、

$$
C = \frac{n}{n - m} \left( \frac{n}{m} \right) ^\frac{m}{n - m}
$$
