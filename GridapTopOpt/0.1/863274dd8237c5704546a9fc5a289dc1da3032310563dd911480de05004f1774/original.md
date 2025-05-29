```
struct HamiltonJacobiEvolution{O}
```

A standard forward Euler in time finite difference method for solving the  Hamilton-Jacobi evolution equation and reinitialisation equation  on order `O` finite elements in serial or parallel. 

Based on the scheme by Osher and Fedkiw ([link](https://doi.org/10.1007/b98879)).

# Parameters

  * `stencil::Stencil`: Spatial finite difference stencil for a single step HJ  equation and reinitialisation equation.
  * `model`: A `CartesianDiscreteModel`.
  * `space`: FE space for level-set function
  * `perm`: A permutation vector
  * `params`: Tuple of additional params
  * `cache`: Stencil cache
