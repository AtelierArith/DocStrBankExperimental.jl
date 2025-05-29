```
prob_pds_brusselator
```

正の保守的な自律非線形PDS

$$
\begin{aligned}
u_1' &= -u_1,\\
u_2' &= -u_2u_5,\\
u_3' &= u_2u_5,\\
u_4' &= u_5,\\
u_5' &= u_1 - u_2u_5 + u_5^2u_6 - u_5,\\
u_6' &= u_2u_5 - u_5^2u_6,
\end{aligned}
$$

初期値 $\mathbf{u}_0 = (10.0, 10.0, 0.0, 0.0, 0.1, 0.1)^T$ と時間領域 $(0.0, 20.0)$。独立した2つの線形不変量があり、例えば $u_1+u_4+u_5+u_6 = 10.2$ と $u_2+u_3 = 10.0$ です。

## 参考文献

  * Luca Bonaventura,  and Alessandro Della Rocca. "Unconditionally Strong Stability Preserving Extensions of the TR-BDF2 Method." Journal of Scientific Computing 70 (2017): 859 - 895. [DOI: 10.1007/s10915-016-0267-9](https://doi.org/10.1007/s10915-016-0267-9)
