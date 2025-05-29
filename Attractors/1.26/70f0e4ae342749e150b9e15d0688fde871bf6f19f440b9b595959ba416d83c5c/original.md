```
basins_fractal_test(basins; ε = 20, Ntotal = 1000) -> test_res, Sbb
```

Perform an automated test to decide if the boundary of the basins has fractal structures based on the method of Puy et al. [Puy2021](@cite). Return `test_res` (`:fractal` or `:smooth`) and the mean basin boundary entropy.

## Keyword arguments

  * `ε = 20`: size of the box to compute the basin boundary entropy.
  * `Ntotal = 1000`: number of balls to test in the boundary for the computation of `Sbb`

## Description

The test "looks" at the basins with a magnifier of size `ε` at random. If what we see in the magnifier looks like a smooth boundary (onn average) we decide that the boundary is smooth. If it is not smooth we can say that at the scale `ε` we have structures, i.e., it is fractal.

In practice the algorithm computes the boundary basin entropy `Sbb` [`basin_entropy`](@ref) for `Ntotal` random boxes of radius `ε`. If the computed value is equal to theoretical value of a smooth boundary (taking into account statistical errors and biases) then we decide that we have a smooth boundary. Notice that the response `test_res` may depend on the chosen ball radius `ε`. For larger size, we may observe structures for smooth boundary and we obtain a *different* answer.

The output `test_res` is a symbol describing the nature of the basin and the output `Sbb` is the estimated value of the boundary basin entropy with the sampling method.
