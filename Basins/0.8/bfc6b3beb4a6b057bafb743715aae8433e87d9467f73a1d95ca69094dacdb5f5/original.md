```
basin_entropy(basin; eps_x=20, eps_y=20)
```

This algorithm computes the basin entropy of a computed basin of attraction on a regular grid. The function return the basin entropy and the boundary basin entropy.

[A. Daza, A. Wagemakers, B. Georgeot, D. Guéry-Odelin and M. A. F. Sanjuán, Basin entropy: a new tool to analyze uncertainty in dynamical systems, Sci. Rep., 6, 31416, (2016).]

## Arguments

  * `basin` : the matrix containing the information of the basin.

## Keyword arguments

  * `eps_x`, `eps_y` : define the size of the box that will be used to sample the basin
