```
mass_matrix_boundary(D::AbstractDerivativeOperator)
```

微分演算子 `D` の境界での質量行列を構築します。古典的な1次元非周期的演算子の場合、これは行列 `Diagonal([-1, 0, ..., 0, 1])` です。周期的1次元演算子の場合、これはゼロ行列です。
