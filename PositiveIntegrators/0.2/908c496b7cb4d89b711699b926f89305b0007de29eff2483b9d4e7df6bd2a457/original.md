```
prob_pds_nonlinmod
```

Positive and conservative autonomous nonlinear PDS

$$
\begin{aligned}
u_1' &= -\frac{u_1u_2}{u_1 + 1.0},\\
u_2' &= \frac{u_1u_2}{u_1 + 1.0} - 0.3u_2,\\
u_3' &= 0.3 u_2,
\end{aligned}
$$

with initial value $\mathbf{u}_0 = (9.98, 0.01, 0.01)^T$ and time domain $(0.0, 30.0)$. There is one independent linear invariant, e.g. $u_1+u_2+u_3 = 10.0$.

## References

  * Hans Burchard, Eric Deleersnijder, and Andreas Meister. "A high-order conservative Patankar-type discretisation for stiff systems of production-destruction equations." Applied Numerical Mathematics 47.1 (2003): 1-30. [DOI: 10.1016/S0168-9274(03)00101-6](https://doi.org/10.1016/S0168-9274(03)00101-6)
