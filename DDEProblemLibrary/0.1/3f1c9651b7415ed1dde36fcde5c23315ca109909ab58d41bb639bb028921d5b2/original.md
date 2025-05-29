```
prob_dde_DDETST_E2
```

Delay differential equation model of a logistic Gauss-type predator-prey system, given by

$$
u_1'(t) = u_1(t) (1 - u_1(t - \tau) - \rho u_1'(t - \tau)) - \frac{u_2(t) u_1(t)^2}{u_1(t)^2 + 1}, 
$$

$$
u_2'(t) = u_2(t) \left(\frac{u_1(t)^2}{u_1(t)^2 + 1} - \alpha\right),
$$

for $t \in [0, 2]$ with history function

$$
\phi_1(t) = 0.33 - t / 10, 
$$

$$
\phi_2(t) = 2.22 + t / 10,
$$

for $t \leq 0$, where $\alpha = 0.1$, $\rho = 2.9$, and $\tau = 0.42$.

# References

Kuang, Y. (1991). On neutral delay logistics Gauss-type predator-prey systems, Dyn. Stab. Systems (6), pp. 173-189.
