```julia
evaluate_GMM(X, GMM, k; ...)
evaluate_GMM(X, GMM, k, dic; compute_symKL, compare_EM)

```

Computes log-likelihood of `GMM` for the data `X`, and the symmetric KL divergence w.r.t. to the generative model if this one is passed as `dic[:non_numerical][:dsGMM]` (TODO: maki this cleaner). If `compare_EM`, then the same quantities are computed for a GMM fitted to the data `X` using the EM algorithm from the `GaussianMixtures` package.
