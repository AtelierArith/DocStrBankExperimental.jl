```
prob_dde_DDETST_F2
```

Delay differential equation

$$
u'(t) = u'(2t - 0.5)
$$

for $t \in [0.25, 0.499]$ with history function $\phi(t) = \exp(-t^2)$ and $\phi'(t) = -2t \exp(-t^2)$ for $t \leq 0.25$.

# Solution

The analytical solution for $t \in [0.25, 0.499]$ is

$$
u(t) = u_i(t) = \exp(-4^i t^2 + B_i t + C_i) / 2^i + K_i
$$

if $t \in [x_i, x_{i + 1}]$, where

$$
x_i = (1 - 2^{-i}) / 2, 
$$

$$
B_i = 2 (4^{i-1} + B_{i-1}), 
$$

$$
C_i = - 4^{i-2} - B_{i-1} / 2 + C_{i-1}, 
$$

$$
K_i = - \exp(-4^i x_i^2 + B_i x_i + C_i) / 2^i + u_{i-1}(x_i),
$$

and $B_0 = C_0 = K_0 = 0$.

# References

Neves, K. W. and Thompson, S. (1992). Solution of systems of functional differential equations with state dependent delays, Technical Report TR-92-009, Computer Science, Radford University.
