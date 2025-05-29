```
interpolation_matrix(poly::AbstractPolynomial, x)
```

`poly`のノードから点`x`への補間行列を返します。例えば：

```
P = Chebyshev2{5}()
x = range(-1, stop=1, length=10)
M = interpolation_matrix(P, x)
```

今、`y(x) ≈ M*y₀` であり、`y(nodes(poly)) = y₀` です。
