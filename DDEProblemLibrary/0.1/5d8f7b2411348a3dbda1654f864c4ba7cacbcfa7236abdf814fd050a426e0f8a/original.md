```
prob_dde_DDETST_G2
```

Delay differential equation

$$
u'(t) = - u'(u(t) - 2)
$$

for $t \in [0, 1]$ with history function $\phi(t) = 1 - t$ for $t \leq 0$ and $\phi'(t) = -1$ for $t < 0$.

# Solution

The analytical solution for $t \in [0, 1]$ is

$$
u(t) = t + 1.
$$

El'sgol'ts, L. E. and Norkin, S. B. (1973). Introduction to the Theory and Application of Differential Equations with Deviating Arguments, Academic Press, New York, pp. 44-45.
