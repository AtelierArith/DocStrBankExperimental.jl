```
prob_pds_linmod
```

Positive and conservative autonomous linear PDS

$$
\begin{aligned}
u_1' &= u_2 - 5u_1,\\
u_2' &= 5u_1 - u_2,
\end{aligned}
$$

with initial value $\mathbf{u}_0 = (0.9, 0.1)^T$ and time domain $(0.0, 2.0)$. There is one independent linear invariant, e.g. $u_1+u_2 = 1$.

## References

  * Hans Burchard, Eric Deleersnijder, and Andreas Meister. "A high-order conservative Patankar-type discretisation for stiff systems of production-destruction equations." Applied Numerical Mathematics 47.1 (2003): 1-30. [DOI: 10.1016/S0168-9274(03)00101-6](https://doi.org/10.1016/S0168-9274(03)00101-6)
