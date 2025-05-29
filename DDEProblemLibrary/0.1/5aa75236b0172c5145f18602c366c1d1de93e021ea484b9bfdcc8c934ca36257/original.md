```
prob_dde_DDETST_F1
```

Delay differential equation

$$
u'(t) = 2 \cos(2t) u(t / 2)^{2 \cos t} + \log(u'(t / 2)) - \log(2 \cos t) - \sin t
$$

for $t \in [0, 1]$ with history function $\phi(0) = 1$ and $\phi'(0) = 2$.

# Solution

The analytical solution for $t \in [0, 1]$ is

$$
u(t) = \exp(\sin(2t)).
$$

# References

Jackiewicz, Z. (1981). One step methods for the numerical solution of Volterra functional differential equations of neutral type, Applicable Anal. (12), pp. 1-11.
