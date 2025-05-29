```
prob_pds_robertson
```

Positive and conservative autonomous nonlinear PDS

$$
\begin{aligned}
u_1' &= -0.04u_1+10^4 u_2u_3,\\
u_2' &=  0.04u_1-10^4 u_2u_3-3⋅10^7 u_2^2,\\
u_3' &= 3⋅10^7 u_2^2,
\end{aligned}
$$

with initial value $\mathbf{u}_0 = (1.0, 0.0, 0.0)^T$ and time domain $(0.0, 10^{11})$. There is one independent linear invariant, e.g. $u_1+u_2+u_3 = 1.0$.

## References

  * Ernst Hairer, Gerd Wanner. "Solving Ordinary Differential Equations II - Stiff and Differential-Algebraic Problems." 2nd Edition, Springer (2002): Section IV.1.
