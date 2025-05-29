```
ridge(X, y, r; ...)
```

Solve the ridge regression problem.

Here, $y$ can be either a vector, or a matrix where each column is a response vector.

The argument `r` gives the quadratic regularization matrix $Q$, which can be in either of the following forms:

  * `r` is a real scalar, then $Q$ is considered to be `r * eye(n)`, where `n` is the dimension of `a`.
  * `r` is a real vector, then $Q$ is considered to be `diagm(r)`.
  * `r` is a real symmetric matrix, then $Q$ is simply considered to be `r`.

This function accepts two keyword arguments:

  * `dims`: whether input observations are stored as rows (`1`) or columns (`2`). (default is `1`)
  * `bias`: whether to include the bias term `b`. (default is `true`)

The function results the solution `a`. In particular, when `y` is a vector (matrix), `a` is also a vector (matrix). If `bias` is true, then the returned array is augmented as `[a; b]`.
