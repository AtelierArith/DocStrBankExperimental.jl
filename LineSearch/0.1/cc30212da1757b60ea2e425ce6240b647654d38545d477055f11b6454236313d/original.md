```
LiFukushimaLineSearch(; lambda_0 = 1, beta = 1 // 2, sigma_1 = 1 // 1000,
    sigma_2 = 1 // 1000, eta = 1 // 10, nan_maxiters::Int = 5, maxiters::Int = 100)
```

A derivative-free line search and global convergence of Broyden-like method for nonlinear equations [li2000derivative](@cite).

!!! tip
    For static arrays and numbers if `nan_maxiters` is either `nothing` or `missing`, we provide a fully non-allocating implementation of the algorithm, that can be used inside GPU kernels. However, this particular version doesn't support `stats` and `reinit!` and those will be ignored. Additionally, we fix the initial alpha for the search to be `1`.

