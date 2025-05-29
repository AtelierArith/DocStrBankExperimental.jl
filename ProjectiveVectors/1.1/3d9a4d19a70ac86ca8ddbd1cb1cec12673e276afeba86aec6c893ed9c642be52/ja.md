```
LinearAlgebra.rmul!(z::PVector{T, N}, λ::NTuple{N, <:Number}) where {T, N}
LinearAlgebra.rmul!(z::PVector{T, 1}, λ::Number) where {T}
```

`z`の各成分`zᵢ`を`λ[i]`で乗算します。
