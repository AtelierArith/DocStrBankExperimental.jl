```
fit_mle(hmm, observations; ...) -> AbstractHMM
```

Estimate the HMM parameters using the EM (Baum-Welch) algorithm, with `hmm` as the initial state.

**Keyword Arguments**

  * `display::Symbol = :none`: when to display convergence logs, can be set to `:iter` or `:final`.
  * `init::Symbol = :none`: if set to `:kmeans` the HMM parameters will be initialized using a K-means clustering.
  * `maxiter::Integer = 100`: maximum number of iterations to perform.
  * `tol::Integer = 1e-3`: stop the algorithm when the improvement in the log-likelihood is less than `tol`.

**Output**

  * `<:AbstractHMM`: a copy of the original HMM with the updated parameters.
