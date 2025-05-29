```
prob_dde_DDETST_C3
```

Delay differential equation model of hematopoiesis, given by

$$
u_1'(t) = \hat{s}_0 u_2(t - T_1) - \gamma u_1(t) - Q,
$$

$$
u_2'(t) = f(u_1(t)) - k u_2(t),
$$

$$
u_3'(t) = 1 - \frac{Q \exp(\gamma u_3(t))}{\hat{s}_0 u_2(t - T_1 - u_3(t))},
$$

for $t \in [0, 300]$ with history function $\phi_1(0) = 3.325$, $\phi_3(0) = 120$, and

$$
\phi_2(t) = \begin{cases}
  10 & \text{if } t \in [- T_1, 0],\\
  9.5 & \text{if } t < - T_1,
\end{cases}
$$

where $f(y) = a / (1 + K y^r)$, $\hat{s}_0 = 0.0031$, $T_1 = 6$, $\gamma = 0.001$, $Q = 0.0275$, $k = 2.8$, $a = 6570$, $K = 0.0382$, and $r = 6.96$.

# References

Mahaffy, J. M., Belair, J. and Mackey, M. C. (1996). Hematopoietic model with moving boundary condition and state dependent delay, Private communication.
