```
prob_pds_npzd
```

Positive and conservative autonomous nonlinear PDS

$$
\begin{aligned}
u_1' &= 0.01u_2 + 0.01u_3 + 0.003u_4 - \frac{u_1u_2}{0.01 + u_1},\\
u_2' &= \frac{u_1u_2}{0.01 + u_1}- 0.01u_2 - 0.5( 1 - e^{-1.21u_2^2})u_3 - 0.05u_2,\\
u_3' &= 0.5(1 - e^{-1.21u_2^2})u_3 - 0.01u_3 - 0.02u_3,\\
u_4' &= 0.05u_2 + 0.02u_3 - 0.003u_4
\end{aligned}
$$

with initial value $\mathbf{u}_0 = (8.0, 2.0, 1.0, 4.0)^T$ and time domain $(0.0, 10.0)$. There is one independent linear invariant, e.g. $u_1+u_2+u_3+u_4 = 15.0$.

## References

  * Hans Burchard, Eric Deleersnijder, and Andreas Meister. "Application of modified Patankar schemes to stiff biogeochemical models for the water column." Ocean Dynamics 55 (2005): 326-337. [DOI: 10.1007/s10236-005-0001-x](https://doi.org/10.1007/s10236-005-0001-x)
