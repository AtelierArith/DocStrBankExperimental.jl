```
prob_dde_DDETST_C2
```

Delay differential equation

$$
u_1'(t) = - 2 u_1(t - u_2(t)),
$$

$$
u_₂'(t) = \frac{|u_1(t - u_2(t))| - |u_1(t)|}{1 + |u_1(t - u_2(t))|},
$$

for $t \in [0, 40]$ with history function

$$
\phi_1(t) = 1,
$$

$$
\phi_2(t) = 0.5,
$$

for $t \leq 0$.

# References

Paul, C. A. H. (1994). A test set of functional differential equations, Technical Report 249, The Department of Mathematics, The University of Manchester, Manchester, England.
