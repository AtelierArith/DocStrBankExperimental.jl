```
llsq(X, y; ...)
```

Solve the linear least square problem.

Here, `y` can be either a vector, or a matrix where each column is a response vector.

This function accepts two keyword arguments:

  * `dims`: whether input observations are stored as rows (`1`) or columns (`2`). (default is `1`)
  * `bias`: whether to include the bias term `b`. (default is `true`)

The function results the solution `a`. In particular, when `y` is a vector (matrix), `a` is also a vector (matrix). If `bias` is true, then the returned array is augmented as `[a; b]`.
