```
prob_dde_RADAR5_waltman
```

Delay differential equation model of antibody production, given by

$$
  u_1'(t) = - r u_1(t) u_2(t) - s u_1(t) u_4(t), 
$$

$$
  u_2'(t) = - r u_1(t) u_2(t) + \alpha r u_1(u_5(t)) u_2(u_5(t)) [t \geq t_0], 
$$

$$
  u_3'(t) = r u_1(t) u_2(t), 
$$

$$
  u_4'(t) = - s u_1(t) u_4(t) - \gamma u_4(t) + \beta r u_1(u_6(t)) u_2(u_6(t)) [t > t_1], 
$$

$$
  u_5'(t) = [t \geq t_0] \frac{u_1(t) u_2(t) + u_3(t)}{u_1(u_5(t)) u_2(u_5(t)) + u_3(u_5(t))}, 
$$

$$
  u_6'(t) = [t \geq t_1] \frac{1e-12 + u_2(t) + u_3(t)}{1e-12 + u_2(u_6(t)) + u_3(u_6(t))},
$$

for $t \in [0, 300]$ with history function

$$
  \phi_1(t) = \phi_0, 
$$

$$
  \phi_2(t) = 1e-15, 
$$

$$
  \phi_3(t) = 0, 
$$

$$
  \phi_4(t) = 0, 
$$

$$
  \phi_5(t) = 0, 
$$

$$
  \phi_6(t) = 0,
$$

for $t \leq 0$, where $\alpha = 1.8$, $\beta = 20$, $\gamma = 0.002$, $r = 5e4$, $s = 1e5$, $t_0 = 32$, $t_1 = 119$, and $\phi_0 = 0.75e-4$.

# References

Waltman, P. (1978). A threshold model of antigen-stimulated antibody production, Theoretical Immunology (8), pp. 437-453.
