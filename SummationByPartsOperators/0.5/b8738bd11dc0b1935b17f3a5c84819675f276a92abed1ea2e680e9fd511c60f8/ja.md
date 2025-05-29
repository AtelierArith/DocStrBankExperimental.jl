```
fourier_derivative_operator(xmin::Real, xmax::Real, N::Integer)
fourier_derivative_operator(; xmin::Real, xmax::Real, N::Integer)
```

`xmin`と`xmax`の間の均一グリッド上に`N`ノードと`N÷2+1`の複素フーリエモードを使用して[`FourierDerivativeOperator`](@ref)を構築します。
