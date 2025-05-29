```
compress(epca::EPCA, X::AbstractMatrix{T}; maxiter::Integer = 100, verbose::Bool = false, steps_per_print::Integer = 10) where T <: Real
```

Compresses the input data `X` with the EPCA model.

# Arguments

  * `epca::EPCA`: The fitted EPCA model.[^1] `fit!` should be called before `compress`.
  * `X::AbstractMatrix{T}`: (`n`, `indim`) - The input data matrix (can differ from the training data). Rows are observations. Columns are features or variables.

# Keyword Arguments

  * `maxiter::Integer = 100`: The maximum number of iterations performed during loss minimization. Defaults to `100`. May converge early.
  * `verbose::Bool = false`: A flag indicating whether to print optimization progress. If set to `true`, prints the loss value and iteration number at specified intervals (`steps_per_print`). Defaults to `false`.
  * `steps_per_print::Integer = 10`: The number of iterations between printed progress updates when `verbose` is set to `true`. For example, if `steps_per_print` is `10`, progress will be printed every 10 iterations. Defaults to `10`.

# Returns

  * `A::AbstractMatrix{T}`: (`n`, `outdim`) - The compressed data.

# Usage

```julia
# Generate some random test data
m = 10
Y = rand(0:1, m, indim)

# Compress the test data using the fitted model from the previous example
Y_compressed = compress(epca, Y)
```

[^1]: If `compress` is called before `fit!`, `X` will compressed using unfitted starting weights.
