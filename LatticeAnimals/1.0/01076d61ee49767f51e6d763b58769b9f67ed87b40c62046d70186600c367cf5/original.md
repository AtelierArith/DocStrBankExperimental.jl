```
Polyomino(n, p)
```

Generate a random polyomino of size n from the percolation distribution at p using the Metropolis algorithm. The basis consits of the two unit-vectors as columns in a matrix. The four neighbours are then specified each as a linear combination of the basis vectors.

# Arguments

```
* `n`: Size of the polyomino
* `p`: Percolation factor in [0, 1)
```
