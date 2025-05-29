# Extended help

```
constraints_list(P::Ball1)
```

### Notes

In $n$ dimensions there are $2^n$ constraints (unless the radius is 0).

### Algorithm

The constraints can be defined as $d_i^T (x-c) ≤ r$ for all $d_i$, where $d_i$ is a vector with elements $1$ or $-1$ in $n$ dimensions. To span all possible $d_i$, the function `Iterators.product` is used.
