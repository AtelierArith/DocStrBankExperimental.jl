```
prob_dde_DDETST_A2
```

Delay differential equation model of chronic granulocytic leukemia, given by

$$
u_1'(t) = \frac{1.1}{1 + \sqrt{10} u_1(t - 20)^{5/4}} - \frac{10 u_1(t)}{1 + 40 u_2(t)},
$$

$$
u_2'(t) = \frac{100 u_1(t)}{1 + 40 u_2(t)} - 2.43 u_2(t),
$$

for $t \in [0, 100]$ and history function

$$
\phi_1(t) = 1.05767027/3,
$$

$$
\phi_2(t) = 1.030713491/3,
$$

for $t \leq 0$.

# References

Wheldon, T., Kirk, J. and Finlay, H. (1974). Cyclical granulopoiesis in chronic granulocytic leukemia: A simulation study., Blood (43), pp. 379-387.
