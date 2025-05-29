### Description

The `momentmatrix` function returns the matrix of moment conditions for the estimation problem defined by `x`. Moment conditions are crucial for various estimation procedures, such as Generalized Method of Moments (GMM) and Maximum Likelihood Estimation (MLE). 

For MLE, the moment matrix corresponds to the inverse of the Hessian of the (pseudo-)log-likelihood function, evaluated at the data. For GMM, it represents the matrix of moment conditions evaluated at the observed data.

This function can be extended to support user-defined types, allowing flexibility for different estimation methods.

### Usage

```julia
momentmatrix(x) -> Matrix
momentmatrix(x, t) -> Matrix
momentmatrix!(x, y) -> Matrix
```

  * `momentmatrix(x)`: Returns the moment matrix for the estimation problem `x`.
  * `momentmatrix(x, t)`: Returns the moment matrix for the estimation problem `x` when the parameter is equal to t.
  * `momentmatrix!(x, y)`: In-place version, updating the matrix `y` with the moment conditions evaluated for `x`.

The matrix returned is typically of size `(obs x m)`, where `obs` refers to the number of observations, and `m` refers to the number of moments. Users can define their own moment matrices for custom types by overloading this function.
