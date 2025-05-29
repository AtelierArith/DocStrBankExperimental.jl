```
prob_pds_robertson
```

正の保守的な自律非線形PDS

$$
\begin{aligned}
u_1' &= -0.04u_1+10^4 u_2u_3,\\
u_2' &=  0.04u_1-10^4 u_2u_3-3⋅10^7 u_2^2,\\
u_3' &= 3⋅10^7 u_2^2,
\end{aligned}
$$

初期値 $\mathbf{u}_0 = (1.0, 0.0, 0.0)^T$ と時間領域 $(0.0, 10^{11})$ を持ちます。独立した線形不変量が1つあります。例えば、$u_1+u_2+u_3 = 1.0$ です。

## 参考文献

  * Ernst Hairer, Gerd Wanner. "Solving Ordinary Differential Equations II - Stiff and Differential-Algebraic Problems." 2nd Edition, Springer (2002): Section IV.1.
