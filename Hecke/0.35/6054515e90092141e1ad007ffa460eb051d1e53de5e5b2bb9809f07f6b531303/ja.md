```
regulator(x::Vector{T}, abs_tol::Int = 64) -> ArbFieldElem
```

ベクトル `x` の要素のレギュレーター $r$ を計算します。$r$ の半径は `-2^abs_tol` より小さくなります。
