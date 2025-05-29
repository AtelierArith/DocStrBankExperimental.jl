```
prob_dde_constant_1delay_ip
```

Delay differential equation

$$
u'(t) = -u(t - 1)
$$

for $t \in [0, 1]$ with history function $\phi(t) = 0$ if $t < 0$ and $\phi(0) = 1$.

# Solution

The analytical solution for $t \in [0, 10]$ can be obtained by the method of steps and is provided in this implementation.
