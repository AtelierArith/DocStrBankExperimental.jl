```
interpolate(poly::AbstractPolynomial, y₀, [x])
```

Return the value of `y(x)` given that `y(nodes(poly)) = y₀`. If the value of `x` is not provided, return a function `y(x)` that evaluates the interpolant at any `x`.
