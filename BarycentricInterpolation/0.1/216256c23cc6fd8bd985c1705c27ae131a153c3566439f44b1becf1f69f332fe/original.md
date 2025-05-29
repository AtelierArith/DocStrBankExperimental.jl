```
interpolation_matrix(poly::AbstractPolynomial, x)
```

Return the interpolation matrix from the nodes of `poly` to the point(s) `x`. For example :

```
P = Chebyshev2{5}()
x = range(-1, stop=1, length=10)
M = interpolation_matrix(P, x)
```

Now `y(x) ≈ M*y₀` given that `y(nodes(poly)) = y₀.
