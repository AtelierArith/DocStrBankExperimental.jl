An algorithm type for `Evolve`

This corresponds to time evolution with exponential approximation WI or WII combined to obtained approximation of the given order

# Examples

```
ApproxW(order = 2)                   order 2, WII
ApproxW(order = 4, w = 1)            order 4, WI
ApproxW(order = 4, n_symmetrize = 3) order 4, make hermitian every 3 steps
```
