```
prob_dde_DDETST_A1
```

Delay differential equation model of blood production, given by

$$
u'(t) = \frac{0.2 u(t - 14)}{1 + u(t - 14)^{10}} - 0.1 u(t)
$$

for $t \in [0, 500]$ and history function $\phi(t) = 0.5$ for $t \leq 0$.

# References

Mackey, M. C. and Glass, L. (1977). Oscillation and chaos in physiological control systems, Science (197), pp. 287-289.
