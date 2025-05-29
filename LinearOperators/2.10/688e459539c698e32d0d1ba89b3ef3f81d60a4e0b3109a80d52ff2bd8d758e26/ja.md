```
LinearOperator(M::Hermitian{T}, S = Vector{T}) where {T}
```

エルミート行列から線形演算子を構築します。要素が実数であれば、対称でもあります。`S`をGPU上のLinearOperatorsを使用するように変更します。
