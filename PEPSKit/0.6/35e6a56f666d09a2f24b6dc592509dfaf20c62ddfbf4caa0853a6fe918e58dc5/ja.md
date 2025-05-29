```
struct InfinitePEPS{T<:PEPSTensor}
```

2D正方格子上の無限投影絡み合ったペア状態を表します。

## フィールド

  * `A::Matrix{T} where T<:(TensorKit.AbstractTensorMap{<:Any, S, 1, 4} where S<:TensorKit.ElementarySpace)`
