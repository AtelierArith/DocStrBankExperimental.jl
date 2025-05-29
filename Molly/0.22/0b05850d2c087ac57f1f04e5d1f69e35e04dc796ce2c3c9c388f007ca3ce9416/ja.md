```
バッキンガム(; cutoff, use_neighbors, shortcut, A_mixing, B_mixing,
           C_mixing, weight_special)
```

二つの原子間のバッキンガム相互作用。

ポテンシャルエネルギーは次のように定義されます。

$$
V(r_{ij}) = A_{ij} \exp(-B_{ij} r_{ij}) - \frac{C_{ij}}{r_{ij}^6}
$$

そして、各原子に対する力は次のように表されます。

$$
\vec{F}_i = \left( A_{ij} B_{ij} \exp(-B_{ij} r_{ij}) - 6 \frac{C_{ij}}{r_{ij}^7} \right) \frac{\vec{r}_{ij}}{r_{ij}}
$$

パラメータは次のように原子パラメータから導出されます。

$$
\begin{aligned}
A_{ij} &= (A_{ii} A_{jj})^{1/2} \\
B_{ij} &= \frac{2}{\frac{1}{B_{ii}} + \frac{1}{B_{jj}}} \\
C_{ij} &= (C_{ii} C_{jj})^{1/2}
\end{aligned}
$$

したがって、この相互作用を使用する原子は、`A`、`B`、および `C` のフィールドを持っている必要があります。
