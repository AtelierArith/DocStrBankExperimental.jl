A look ahead estimator associated with a given stochastic kernel `p` and a vector of observations `X`.

##### Fields

  * `p::Function`: The stochastic kernel. Signature is `p(x, y)` and it should be vectorized in both inputs
  * `X::Matrix`: A vector containing observations. Note that this can be passed as any kind of `AbstractArray` and will be coerced into an `n x 1` vector.
