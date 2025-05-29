```
scan(y, g, K, nperm, nprocs, rndseed, reml)
```

Performs genome scan on a number of resamples from permuting an univariate trait with each genome marker (one-df test). Variance components  are estimated from the null model and assumed to be the same across markers.

# Arguments

  * y = 1d array of floats consisting of the N observations for a certain quantitative trait (dimension: N*1)
  * g = 2d array of floats consisting of all p gene markers (dimension: N*p)
  * K = 2d array of floats consisting of the genetic relatedness of the N observations (dimension:N*N)

# Keyword arguments

  * nperms = Number of permutations requested
  * nprocs = Number of concurrent processes
  * rndseed = Random seed for perform permutations
  * reml = Boolean flag indicating if variance components will be estimated by REML (true) or ML (false)

# Value

  * lod = 2d array of floats consisting of the LOD scores for each permuted trait (row) and the markers (columns).

# Some notes
