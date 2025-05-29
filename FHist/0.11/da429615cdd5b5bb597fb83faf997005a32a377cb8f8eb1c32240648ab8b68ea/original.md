```
bayes_rebin_edges(h::Hist1D; prior=BayesHistogram.Geometric(0.995))
```

Find optimal bin edges for a histogram using Bayesian rebinning algorithm. This function only find edges, it doesn't return a new histogram.

For possible priors, see [`BayesHistogram.jl`](https://github.com/francescoalemanno/BayesHistogram.jl/blob/main/src/BayesHistogram.jl).
