```
isotonic(x, y[, w])
```

Solve the isotonic regression problem using the pool adjacent violators algorithm[^1].

Here `x` is the regressor vector, `y` is response vector, and `w` is an optional weights vector.

The function returns a prediction vector of the same size as the regressor vector `x`.
