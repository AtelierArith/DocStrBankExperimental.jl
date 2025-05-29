```
orthonormal_range(A::AbstractMatrix{T}; tol::T=nothing) where {T<:Number}
```

`A`の範囲の直交正規基底。`A`がスパースであり、`T`が[`Float64`, `ComplexF64`, `Float32`, `ComplexF32`]のいずれかに属する場合、QR因子分解を使用し、スパースな結果を返します。それ以外の場合はSVDを使用し、密な行列を返します。許容誤差`tol`はランクを計算するために使用され、提供されていない場合は自動的に設定されます。
