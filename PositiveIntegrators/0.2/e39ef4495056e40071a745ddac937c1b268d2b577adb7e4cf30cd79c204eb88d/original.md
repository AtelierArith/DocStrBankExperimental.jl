```
prob_pds_sir
```

Positive and conservative autonomous nonlinear PDS

$$
\begin{aligned}
u_1' &= -2u_1u_2,\\
u_2' &= 2u_1u_2 - u_2,\\
u_3' &= u_2,
\end{aligned}
$$

with initial value $\mathbf{u}_0 = (0.99, 0.005, 0.005)^T$ and time domain $(0.0, 20.0)$. There is one independent linear invariant, e.g. $u_1+u_2+u_3 = 1.0$.

## References

  * Ronald E. Mickens, and Talitha M. Washington. "NSFD discretizations of interacting population models satisfying conservation laws." Computers and Mathematics with Applications 66 (2013): 2307-2316. [DOI: 10.1016/j.camwa.2013.06.011](https://doi.org/10.1016/j.camwa.2013.06.011)
