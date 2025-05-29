```
FockBasis(N,offset=0)
```

Basis for a Fock space where `N` specifies a cutoff, i.e. what the highest included fock state is. Similarly, the `offset` defines the lowest included fock state (default is 0). Note that the dimension of this basis is `N+1-offset`.
