```
prob_pds_bertolazzi
```

正の保守的な自律非線形PDS

$$
\begin{aligned}
\mathbf{u}'=\begin{pmatrix}2 &-1 &-1\\-1 &2 &-1\\-1& -1& 2\end{pmatrix}\begin{pmatrix}5u_2u_3/(10^{-2} + (u_2u_3)^2) + u_2u_3/(10^{-16} + u_2u_3(10^{-8} + u_2u_3))\\
10u_1u_3^2\\
0.1(u_3 - u_2 - 2.5)^2u_1u_2\end{pmatrix}
\end{aligned}
$$

初期値は $\mathbf{u}_0 = (0.0, 1.0, 2.0)^T$ で、時間領域は $(0.0, 1.0)$ です。独立した線形不変量が1つあります。例えば、$u_1+u_2+u_3 = 3.0$ です。

## 参考文献

  * Enrico Bertolazzi. "Positive and conservative schemes for mass action kinetics." Computers and Mathematics with Applications 32 (1996): 29-43. [DOI: 10.1016/0898-1221(96)00142-3](https://doi.org/10.1016/0898-1221(96)00142-3)
