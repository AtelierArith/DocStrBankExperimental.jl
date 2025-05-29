```
inflate(f::MPolyRingElem{T}, defl::Vector{Int}) where T <: RingElement
```

与えられたデフレーション指数（各変数に対して1つのインフレーション係数の配列として供給される）によって指数がインフレート（乗算）されたが、$f$と同じ係数を持つ多項式を返します。
