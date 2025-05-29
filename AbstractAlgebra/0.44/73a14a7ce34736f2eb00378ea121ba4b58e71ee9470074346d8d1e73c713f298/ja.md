```
inflate(f::MPolyRingElem{T}, shift::Vector{Int}, defl::Vector{Int}) where T <: RingElement
```

与えられたデフレーション指数（各変数ごとに1つのインフレーション係数として供給される配列）によって指数がインフレート（乗算）され、その後与えられたシフト（再び各変数ごとに1つのシフトとして供給される配列）によって増加した同じ係数を持つ多項式を返します。
