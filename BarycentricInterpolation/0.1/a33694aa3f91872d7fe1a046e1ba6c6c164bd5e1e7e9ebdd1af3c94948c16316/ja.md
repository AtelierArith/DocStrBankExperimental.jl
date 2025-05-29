```
interpolate(poly::AbstractPolynomial, y₀, [x])
```

`y(nodes(poly)) = y₀` が与えられたときの `y(x)` の値を返します。`x` の値が提供されていない場合は、任意の `x` で補間関数を評価する `y(x)` を返します。
