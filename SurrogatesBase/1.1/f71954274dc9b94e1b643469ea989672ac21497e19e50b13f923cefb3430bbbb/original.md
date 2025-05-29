```
finite_posterior(s::AbstractStochasticSurrogate, xs::AbstractVector)
```

Return a posterior distribution at points `xs`.

An `AbstractStochasticSurrogate` might implement some or all of the following methods on the returned object:

  * `mean(finite_posterior(s,xs))` returns a `Vector` of posterior means at `xs`
  * `var(finite_posterior(s,xs))` returns a `Vector` of posterior variances at `xs`
  * `mean_and_var(finite_posterior(s,xs))` returns a `Tuple` consisting of a `Vector` of posterior means and a `Vector` of posterior variances at `xs`
  * `rand(finite_posterior(s,xs))` returns a `Vector`, which is a sample from the joint

posterior at points `xs`

Use `mean(finite_posterior(s, eachslice(X, dims = 2)))` if `X` is a matrix.
