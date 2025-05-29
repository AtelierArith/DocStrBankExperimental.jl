```
prob_pds_stratreac
```

Positive and nonconservative autonomous nonlinear PDS

$$
\begin{aligned}
u_1' &= r_5 - r_6 -  r_7,\\
u_2' &= 2r_1 - r_2 + r_3 - r_4 + r_6 - r_9 + r_{10} - r_{11},\\
u_3' &= r_2 - r_3 - r_4 - r_5 - r_7 - r_8,\\
u_4' &= -r_1 -r_2 + r_3 + 2r_4+r_5+2r_7+r_8+r_9,\\
u_5' &= -r_8+r_9+r_{10}-r_{11},\\
u_6' &= r_8-r_9-r_{10}+r_{11},
\end{aligned}
$$

with reaction rates

$$
\begin{aligned}
r_1 &=2.643⋅ 10^{-10}σ^3 u_4, & r_2 &=8.018⋅10^{-17}u_2 u_4 , & r_3 &=6.12⋅10^{-4}σ u_3,\\
r_4 &=1.567⋅10^{-15}u_3 u_2 , & r_5 &= 1.07⋅ 10^{-3}σ^2u_3,  & r_6 &= 7.11⋅10^{-11}⋅ 8.12⋅10^6 u_1,\\
r_7 &= 1.2⋅10^{-10}u_1 u_3, & r_8 &= 6.062⋅10^{-15}u_3 u_5, & r_9 &= 1.069⋅10^{-11}u_6 u_2,\\
r_{10} &= 1.289⋅10^{-2}σ u_6, & r_{11} &= 10^{-8}u_5 u_2,
\end{aligned}
$$

where

$$
\begin{aligned}
T &= t/3600 \mod 24,\quad T_r=4.5,\quad T_s = 19.5,\\
σ(T) &= \begin{cases}1, & T_r≤ T≤ T_s,\\0, & \text{otherwise}.\end{cases}
\end{aligned}
$$

The initial value is $\mathbf{u}_0 = (9.906⋅10^1, 6.624⋅10^8, 5.326⋅10^{11}, 1.697⋅10^{16}, 4⋅10^6, 1.093⋅10^9)^T$ and the time domain $(4.32⋅ 10^{4}, 3.024⋅10^5)$. There are two independent linear invariants, e.g. $u_1+u_2+3u_3+2u_4+u_5+2u_6=(1,1,3,2,1,2)\cdot\mathbf{u}_0$ and $u_5+u_6 = 1.097⋅10^9$.

## References

  * Stephan Nüsslein, Hendrik Ranocha, and David I. Ketcheson. "Positivity-preserving adaptive Runge-Kutta methods." Communications in Applied Mathematics and Computer Science 16 (2021): 155-179. [DOI: 10.2140/camcos.2021.16.155](https://doi.org/10.2140/camcos.2021.16.155)
