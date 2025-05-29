```
prob_dde_RADAR5_oregonator
```

Delay differential equation model from chemical kinetics, given by

$$
  u_1'(t) = - k_1 A u_2(t) - k_2 u_1(t) u_2(t - \tau) + k_3 B u_1(t) - 2 k_4 u_1(t)^2, 
$$

$$
  u_2'(t) = - k_1 A u_2(t) - k_2 u_1(t) u_2(t - \tau) + f k_3 B u_1(t),
$$

for $t \in [0, 100.5]$ with history function

$$
  \phi_1(t) = 1e-10, 
$$

$$
  \phi_2(t) = 1e-5,
$$

for $t \leq 0$, where $k_1 = 1.34$, $k_2 = 1.6e9$, $k_3 = 8000$, $k_4 = 4e7$, $k_5 = 1$, $f = 1$, $A = 0.06$, $B = 0.06$, and $\tau = 0.15$.

# References

Epstein, I. and Luo, Y. (1991). Differential delay equations in chemical kinetics. Nonlinear models, Journal of Chemical Physics (95), pp. 244-254.
