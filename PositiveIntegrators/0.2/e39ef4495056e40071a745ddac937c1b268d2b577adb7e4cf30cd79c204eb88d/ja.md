```
prob_pds_sir
```

正の保守的自律非線形PDS

$$
\begin{aligned}
u_1' &= -2u_1u_2,\\
u_2' &= 2u_1u_2 - u_2,\\
u_3' &= u_2,
\end{aligned}
$$

初期値 $\mathbf{u}_0 = (0.99, 0.005, 0.005)^T$ と時間領域 $(0.0, 20.0)$ があります。独立した線形不変量が1つあります。例えば、$u_1+u_2+u_3 = 1.0$ です。

## 参考文献

  * Ronald E. Mickens, and Talitha M. Washington. "NSFD discretizations of interacting population models satisfying conservation laws." Computers and Mathematics with Applications 66 (2013): 2307-2316. [DOI: 10.1016/j.camwa.2013.06.011](https://doi.org/10.1016/j.camwa.2013.06.011)
