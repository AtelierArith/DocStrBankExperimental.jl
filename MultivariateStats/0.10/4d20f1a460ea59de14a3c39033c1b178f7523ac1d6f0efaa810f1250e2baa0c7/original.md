```
fit(MetricMDS, X; kwargs...)
```

Compute an embedding of `X` points by (non)metric multidimensional scaling (MDS).

**Keyword arguments:**

Let `(d, n) = size(X)` be respectively the input dimension and the number of observations:

  * `distances`: The choice of input (*required*):

      * `false`: use `X` to calculate dissimilarity matrix using Euclidean distance
      * `true`: use `X` input as precomputed dissimilarity symmetric matrix (distances)
  * `maxoutdim`: Maximum output dimension (*default* `d-1`)
  * `metric` : a function for calculation of disparity values

      * `nothing`: use dissimilarity values as the disparities to perform the metric MDS (*default*)
      * `isotonic`: converts dissimilarity values to ordinal disparities to perform non-metric MDS
      * any two parameter disparity transformation function, where the first parameter is a vector of proximities (i.e. dissimilarities) and the second parameter is a vector of distances, e.g. `(p,d)->b*p` for some `b` is a transformation function for *ratio* MDS.
  * `tol`: Convergence tolerance (*default* `1.0e-3`)
  * `maxiter`: Maximum number of iterations (*default* `300`)
  * `initial`: an initial reduced space point configuration

      * `nothing`: then an initial configuration is randomly generated (*default*)
      * pre-defined matrix
  * `weights`: a weight matrix

      * `nothing`: then weights are set to one, $w_{ij} = 1$ (*default*)
      * pre-defined matrix

*Note:* if the algorithm is unable to converge then `ConvergenceException` is thrown.
