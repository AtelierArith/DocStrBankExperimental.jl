```
prob_dde_DDETST_D1
```

Delay differential equation

$$
u_1'(t) = u_2(t), 
$$

$$
u_2'(t) = - u_2(\exp(1 - u_2(t))) u_2(t)^2 \exp(1 - u_2(t)),
$$

for $t \in [0.1, 5]$ with history function

$$
\phi_1(t) = \log t, 
$$

$$
\phi_2(t) = 1 / t,
$$

for $t \in (0, 0.1]$.

# Solution

The analytical solution for $t \in [0.1, 5]$ is

$$
u_1(t) = \log t, 
$$

$$
u_2(t) = 1 / t.
$$

# References

Neves, K. W. (1975). Automatic integration of functional differential equations: An approach, ACM Trans. Math. Soft. (1), pp. 357-368.
