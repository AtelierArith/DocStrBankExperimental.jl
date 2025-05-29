```
relative_error(c, d, p=2)
```

Compute the relative error between `c` and `d` with norm `p`, defined as

$$
\beq
\mathrm{rel \, error} = \frac{\left ( int_{-L}^0 (c-d)^p \, \mathrm{d} z \right )^(1/p)}
                             {\left ( int_{-L}^0 d^p \, \mathrm{d} z \right )^(1/p)}
\eeq
$$
