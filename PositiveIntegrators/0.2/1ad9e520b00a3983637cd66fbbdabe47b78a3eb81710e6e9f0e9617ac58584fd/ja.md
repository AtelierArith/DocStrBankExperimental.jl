```
prob_pds_linmod
```

正の保守的自律線形PDS

$$
\begin{aligned}
u_1' &= u_2 - 5u_1,\\
u_2' &= 5u_1 - u_2,
\end{aligned}
$$

初期値 $\mathbf{u}_0 = (0.9, 0.1)^T$ と時間領域 $(0.0, 2.0)$ があります。独立した線形不変量が1つあります。例えば、$u_1+u_2 = 1$ です。

## 参考文献

  * Hans Burchard, Eric Deleersnijder, and Andreas Meister. "A high-order conservative Patankar-type discretisation for stiff systems of production-destruction equations." Applied Numerical Mathematics 47.1 (2003): 1-30. [DOI: 10.1016/S0168-9274(03)00101-6](https://doi.org/10.1016/S0168-9274(03)00101-6)
