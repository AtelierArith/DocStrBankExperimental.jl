```
mutualinfo(pts, marginalinds_x, marginalinds_y, kernel::Kernel = GaussianKernel(); 
    b = 2, kwargs...)
```

Estimate the mutual information using a kernel density estimator. 

## Arguments

  * **`pts`**: The points in the joint space. If computing the mutual information between    two scalar data series `X` and `Y`, the points would be 2-dimensional. It is also    possible to provide higher-dimensional points and compute the mutual information    between only some of the coordinate axes, using `marginalinds_x` and `marginalinds_y`   to indicate which marginals to consider.
  * **`marginalinds_x`**: The indices of the first marginal.
  * **`marginalinds_y`**: The indices of the second marginal.
  * **`kernel`**: An instance of a valid kernel. Defaults to `BoxKernel()`.

## Keyword arguments

  * **`b`**: The base of the logarithm, which determines the unit of information (e.g.    `b = 2` gives the information in bits).
