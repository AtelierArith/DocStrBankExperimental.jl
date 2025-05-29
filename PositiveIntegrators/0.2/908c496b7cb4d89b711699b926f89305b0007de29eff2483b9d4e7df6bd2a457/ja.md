```
prob_pds_nonlinmod
```

正の保守的自律非線形PDS

$$
\begin{aligned}
u_1' &= -\frac{u_1u_2}{u_1 + 1.0},\\
u_2' &= \frac{u_1u_2}{u_1 + 1.0} - 0.3u_2,\\
u_3' &= 0.3 u_2,
\end{aligned}
$$

初期値 $\mathbf{u}_0 = (9.98, 0.01, 0.01)^T$ と時間領域 $(0.0, 30.0)$ を持ちます。独立した線形不変量が1つあります。例えば、$u_1+u_2+u_3 = 10.0$ です。

## 参考文献

  * Hans Burchard, Eric Deleersnijder, and Andreas Meister. "A high-order conservative Patankar-type discretisation for stiff systems of production-destruction equations." Applied Numerical Mathematics 47.1 (2003): 1-30. [DOI: 10.1016/S0168-9274(03)00101-6](https://doi.org/10.1016/S0168-9274(03)00101-6)
