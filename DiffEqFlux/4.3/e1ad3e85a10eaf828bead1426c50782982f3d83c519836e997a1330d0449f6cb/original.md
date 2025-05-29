FFJORD can be used as a distribution to generate new samples by `rand` or estimate densities by `pdf` or `logpdf` (from `Distributions.jl`).

Arguments:

  * `model`: A FFJORD instance.
  * `regularize`: Whether we use regularization (default: `false`).
  * `monte_carlo`: Whether we use monte carlo (default: `true`).
