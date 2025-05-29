```
legendre_second_derivative_operator(xmin::Real, xmax::Real, N::Integer)
legendre_second_derivative_operator(; xmin::Real, xmax::Real, N::Integer)
```

`xmin`と`xmax`の間の均一グリッド上に`N`ノードと`N-1`レジェンドルモードを使用して`LegendreDerivativeOperator`を構築します。
