```
shapley(predict, a, X)
shapley(predict, a, X, j)
shapley(predict, a, X, Z)
shapley(predict, a, X, j, Z)
```

Compute the Shapley values of the points in a dataset `Z`, using the dataset `X` as an empirical estimate of the distribution of the points in `Z`.  If `Z` is not provided, Shapley values will be computed for the points in `X`.  There are a variety of inequivalent methods for computing Shapley values, and these should be specified with `a`, a `Shapley.Algorithm` object which specifies how the computation should be done.  The `predict` function will be used to make predictions on the dataset.  The model object being evaluated is encoded via the `predict` function.

If the prediction returned by `predict` is deterministic, and therefore an array of numbers, the returned Shapley values will be numerical.  If the prediction is probabilistic, it is expected that `predict` returns an array of `Distributions.Sampleable` objects and `Shapley` will return a table.  The columns of this table will be named according to the domain of the distributions returned, as determined via `Distributions.support`.

All algorithms will assume that the function `predict` is most efficient when operating on batches of data.  That is, they will attempt to minimize the number of separate calls to `predict`.

See the [Shapley.jl documentation](https://expandingman.gitlab.io/Shapley.jl/) for more details and examples.

## Arguments

  * `predict`: A function which takes a Tables compatible object (or a matrix) and returns a vector of determinstic predictions   as real numbers or of probabilistic predictions as `Distributions.Sampleable` objects.
  * `a`: A `Shapley.Algorithm` object which specifies how the computation should be performed. See `subtypes(Shapley.Algorithm)`   for a list of available algorithms.
  * `X`: An input dataset which is used by the Shapley algorithms for the purpose of providing an empirical estimation of the   distribution of independent variables.  Typically this would be a test or training set.
  * `j`: The feature to calculate the Shapley values for, as a column of `X`. Should be an integer or `Symbol`.  If not   provided, Shapley values will be computed for all columns.
  * `Z`: The set of data points to compute the Shapley values of.  If not provided, `X` will be used.

## Examples

```julia
m = machine(RandomForestRegressor(), X, y)  # an MLJ machine object
ϕ = shapley(ξ -> predict(m, ξ), Shapley.MonteCarlo(512), X)
```
