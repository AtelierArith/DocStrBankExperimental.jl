```
prob_dde_DDETST_H2
```

Delay differential equation

$$
u'(t) = \cos(t) (1 + u(t u(t)^2)) + L_3 u(t) u'(t u(t)^2) + (1 - L_3) \sin(t) \cos(t \sin(t)^2) - \sin(t + t \sin(t)^2)
$$

for $t \in [0, \pi]$ with history function $\phi(0) = 0$ and $\phi'(0) = 1$, where $L_3 = 0.1$.

# Solution

The analytical solution for $t \in [0, \pi]$ is

$$
u(t) = \sin(t).
$$

# References

Hayashi, H. (1996). Numerical solution of retarded and neutral delay differential equations using continuous Runge-Kutta methods, PhD thesis, Department of Computer Science, University of Toronto, Toronto, Canada.
