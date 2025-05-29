```
FourierDerivativeOperator(xmin::T, xmax::T, N::Integer) where {T<:Real}
```

`xmin`と`xmax`の間の均一グリッド上に`N`ノードと`N÷2+1`の複素フーリエモードを使用して`FourierDerivativeOperator`を構築します。

[`fourier_derivative_operator`](@ref)も参照してください。
