```
prob_dde_DDETST_C4
```

Delay differential equation model of hematopoiesis, given by the same delay differential equation as [`prob_dde_DDETST_C3`](@ref)

$$
u_1'(t) = \hat{s}_0 u_2(t - T_1) - \gamma u_1(t) - Q,
$$

$$
u_2'(t) = f(u_1(t)) - k u_2(t),
$$

$$
u_3'(t) = 1 - \frac{Q \exp(\gamma u_3(t))}{\hat{s}_0 u_2(t - T_1 - u_3(t))},
$$

for $t \in [0, 100]$ with history function $\phi_1(0) = 3.5$, $\phi_3(0) = 50$, and $\phi_2(t) = 10$ for $t \leq 0$, where $f(y) = a / (1 + K y^r)$, $\hat{s}_0 = 0.00372$, $T_1 = 3$, $\gamma = 0.1$, $Q = 0.00178$, $k = 6.65$, $a = 15600$, $K = 0.0382$, and $r = 6.96$.

# References

Mahaffy, J. M., Belair, J. and Mackey, M. C. (1996). Hematopoietic model with moving boundary condition and state dependent delay, Private communication.
