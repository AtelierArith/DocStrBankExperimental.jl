```
integrate_boundary([func = identity,] u, D::AbstractDerivativeOperator)
```

関数 `func` を係数 `u` にマッピングし、境界に沿って積分します。古典的な1D演算子の場合、これは `func(u[end]) - func(u[begin])` です。周期的な1D演算子の場合、これはゼロです。
