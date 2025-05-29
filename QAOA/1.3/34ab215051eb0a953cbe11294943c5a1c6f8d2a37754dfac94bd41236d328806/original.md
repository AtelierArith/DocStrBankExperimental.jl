```
sherrington_kirkpatrick(variance::Float64; seed::Float64=1.0, num_layers::Int=1, driver=X)
```

Wrapper function setting up an instance of the Sherrington-Kirkpatrick model.

### Input

  * `N::Int`: The number of spins of the problem.
  * `variance::Float64`: The variance of the distribution of the coupling matrix.
  * `seed::Float64=1.0`: The seed for the random-number generator used in the coupling matrix.
  * `num_layers::Int=1` (optional): The number of QAOA layers usually denoted by $p$.
  * `driver=X` (optional): The driver or mixer used in the QAOA.

### Output

  * An instance of the `Problem` struct holding all relevant quantities.

### Notes

The cost function of the Sherrington-Kirkpatrick model is

$\hat H_P = \frac{1}{\sqrt{N}}\sum_{i<j\leq N} J_{ij} \hat{Z}_i \hat{Z}_j,$

where the couplings $J_{ij}$ are i.i.d. standard Gaussian variables,  i.e. with zero mean $\langle J_{ij} \rangle = 0$ and variance $\langle J_{ij}^2 \rangle = J^2$.
