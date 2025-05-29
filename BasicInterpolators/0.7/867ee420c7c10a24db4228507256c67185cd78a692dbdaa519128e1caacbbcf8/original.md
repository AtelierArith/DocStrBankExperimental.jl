```
vandermonde(x, y)
```

Generate the coefficients of an arbitrary order polynomial passing through the ponts defined by coordinates `x` and value `y`. For n points, n coefficients $[c_0, c_1, ..., c_{n-1}]$ are returned forming the polynomial $c_0 + c_1x + ... + c_{n-1}x^{n-1}$

!!! warning
    Solving for the the coefficients of a high-order polynomial is a notoriously ill-conditioned problem. It is not recommended for orders greater than 5 or 6, although it depends on the application. If you must interpolate with a high-order polynomial, it's better to use the [`neville`](@ref) function instead of computing coefficients.

