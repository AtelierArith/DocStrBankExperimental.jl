```
prob_dde_DDETST_B1
```

Delay differential equation

$$
u'(t) = 1 - u(\exp(1 - 1/t))
$$

for $t \in [0.1, 10]$ with history function $\phi(t) = \log t$ for $t \in (0, 0.1]$.

# Solution

The analytical solution for $t \in [0.1, 10]$ is

$$
u(t) = \log t.
$$

# References

Neves, K. W. (1975). Automatic integration of functional differential equations: An approach, ACM Trans. Math. Soft. (1), pp. 357-368.
