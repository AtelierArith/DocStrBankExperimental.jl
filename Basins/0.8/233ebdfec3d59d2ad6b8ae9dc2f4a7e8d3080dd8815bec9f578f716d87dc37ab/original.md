```
box_counting_dim(xg, yg, basin; kwargs...)
```

This function compute the box-counting dimension of the boundary. It is related to the uncertainty dimension.

[C. Grebogi, S. W. McDonald, E. Ott, J. A. Yorke, Final state sensitivity: An obstruction to predictability, Physics Letters A, 99, 9, 1983]

## Arguments

  * `basin` : the matrix containing the information of the basin.
  * `xg`, `yg` : 1-dim range vector that defines the grid of the initial conditions to test.

## Keyword arguments

  * `kwargs...` these arguments are passed to `generalized_dim` see `ChaosTools.jl` for the docs.
