```
basins_fractal_dimension(basins; kwargs...) -> V_ε, N_ε, d
```

Estimate the fractal dimension `d` of the boundary between basins of attraction using a box-counting algorithm for the boxes that contain at least two different basin IDs.

## Keyword arguments

  * `range_ε = 2:maximum(size(basins))÷20` is the range of sizes of the box to test (in pixels).

## Description

The output `N_ε` is a vector with the number of the balls of radius `ε` (in pixels) that contain at least two initial conditions that lead to different attractors. `V_ε` is a vector with the corresponding size of the balls. The output `d` is the estimation of the box-counting dimension of the boundary by fitting a line in the `log.(N_ε)` vs `log.(1/V_ε)` curve. However it is recommended to analyze the curve directly for more accuracy.

It is the implementation of the popular algorithm of the estimation of the box-counting dimension. The algorithm search for a covering the boundary with `N_ε` boxes of size `ε` in pixels.
