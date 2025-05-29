```
Polyhex(n, p)
```

Generate a random polyhex of size n from the percolation distribution at p using the Metropolis algorithm. The basis consits of the first unit vector and the vector of length 1 at 120 degrees to the left. The six neighbours are then specified each as a linear combination of the basis vectors.

# Arguments

```
* `n`: Size of the polyhex
* `p`: Percolation factor in [0, 1)
```
