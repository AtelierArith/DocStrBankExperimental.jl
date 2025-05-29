```
kerneldensity(pts, gridpts, kernel::BoxKernel; 
    h = silverman_rule(pts), 
    metric::Metric = Chebyshev(), 
    normalise = true)
```

Naive kernel density estimator (Steuer et al., 2002).

## Arguments

  * **`pts`**: The points for which to evaluate the density.
  * **`gridpts`**: A set of grid point on which to evaluate the density.
  * **`kernel`**: A `Kernel` type. Defaults to `BoxKernel`. Can also be    `GaussianKernel`.

## Keyword arguments

  * **`h`**: The bandwidth. Uses Silverman's rule to compute an optimal    bandwidth assuming a Gaussian density (note: we're not using   a Gaussian kernel here, so might be off).
  * **`gridpts`**: A set of grid point on which to evaluate the density.
  * **`normalise`**: Normalise the density so that it sums to 1.
  * **`metric`**: A instance of a valid metric from `Distances.jl` that is    nonnegative, symmetric and satisfies the triangle inequality. Defaults to    `metric = Chebyshev()`.

## Returns

A density estimate for each grid point.

## References

Steuer, R., Kurths, J., Daub, C.O., Weise, J. and Selbig, J., 2002. The mutual information:  detecting and evaluating dependencies between variables. Bioinformatics, 18(suppl_2), pp.S231-S240.
