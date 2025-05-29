```
hesse!(m::Minuit, ncall::Int=0)
```

Run Hesse algorithm to compute asymptotic errors.

The Hesse method estimates the covariance matrix by inverting the matrix of [second derivatives (Hesse matrix) at the minimum](https://en.wikipedia.org/wiki/Hessian_matrix).  To get parameters correlations, you need to use this. The Minos algorithm is another way to  estimate parameter uncertainties, see function `minos`.

## Arguments

  * `ncall::Int=0` : Approximate upper limit for the number of calls made by the Hesse algorithm. If set to 0, use the adaptive heuristic from the Minuit2 library.

## Notes

The covariance matrix is asymptotically (in large samples) valid. By valid we mean that confidence intervals constructed from the errors contain the true value with a well-known coverage probability (68 % for each interval). In finite samples, this is likely to be true if your cost function looks like a hyperparabola around the minimum.

In practice, the errors very likely have correct coverage if the results from Minos and Hesse methods agree. It is possible to construct artificial functions where this rule is violated, but in practice it should always work.
