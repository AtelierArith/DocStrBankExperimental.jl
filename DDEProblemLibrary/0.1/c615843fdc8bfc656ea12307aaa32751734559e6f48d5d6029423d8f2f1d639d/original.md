```
prob_dde_RADAR5_robertson
```

Delay differential equation model of a chemical reaction with steady state solution, given by

$$
  u_1'(t) = - a u_1(t) + b u_2(t - \tau) u_3(t), 
$$

$$
  u_2'(t) = a u_1(t) - b u_2(t - \tau) u_3(t) - c u_2(t)^2, 
$$

$$
  u_3'(t) = c u_2(t)^2,
$$

for $t \in [0, 10e10]$ with history function $\phi_1(0) = 1$, $\phi_2(t) = 0$ for $t \in [-\tau, 0]$, and $\phi_3(0) = 0$, where $a = 0.04$, $b = 10_000$, $c = 3e7$, and $\tau = 0.01$.

# References

Guglielmi, N. and Hairer, E. (2001). Implementing Radau IIA methods for stiff delay differential equations, Computing (67), pp. 1-12.
