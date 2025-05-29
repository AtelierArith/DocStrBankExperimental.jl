```
fit_mle(mix::MixtureModel, y::AbstractVecOrMat, weights...; method = ClassicEM(), display=:none, maxiter=1000, atol=1e-3, rtol=nothing, robust=false, infos=false)
```

Use the an Expectation Maximization (EM) algorithm to maximize the Loglikelihood (fit) the mixture with an i.i.d sample `y`. The `mix` input is a mixture that is used to initilize the EM algorithm.

  * `weights` when provided, it will compute a weighted version of the EM. (Useful for fitting mixture of mixtures)
  * `method` determines the algorithm used.
  * `infos = true` returns a `Dict` with informations on the algorithm (converged, iteration number, loglikelihood).
  * `robust = true` will prevent the (log)likelihood to overflow to `-∞` or `∞`.
  * `atol` criteria determining the convergence of the algorithm. If the Loglikelihood difference between two iteration `i` and `i+1` is smaller than `atol` i.e. `|ℓ⁽ⁱ⁺¹⁾ - ℓ⁽ⁱ⁾|<atol`, the algorithm stops.
  * `rtol` relative tolerance for convergence, `|ℓ⁽ⁱ⁺¹⁾ - ℓ⁽ⁱ⁾|<rtol*(|ℓ⁽ⁱ⁺¹⁾| + |ℓ⁽ⁱ⁾|)/2` (does not check if `rtol` is `nothing`)
  * `display` value can be `:none`, `:iter`, `:final` to display Loglikelihood evolution at each iterations `:iter` or just the final one `:final`
