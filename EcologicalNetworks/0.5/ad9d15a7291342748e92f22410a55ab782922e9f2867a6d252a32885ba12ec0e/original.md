```
n_random_modules(n::Int64)
```

This returns *a function* which, when applied to a network, will randomly assign every species to one of `n` modules. The correct way to apply this function to a network `N` is, therefore `n_random_modules(4)(N)` (with four modules).

#### References

Thébault, E., 2013. Identifying compartments in presence–absence matrices and bipartite networks: insights into modularity measures. Journal of Biogeography 40, 759–768. https://doi.org/10.1111/jbi.12015
