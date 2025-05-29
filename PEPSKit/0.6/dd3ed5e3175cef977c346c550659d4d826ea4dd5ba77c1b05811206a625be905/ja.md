```
struct InfinitePEPO{T<:PEPOTensor}
```

3D立方格子上の無限投影絡み合ったペア演算子（PEPO）を表します。

## フィールド

  * `A::Array{T, 3} where T<:(TensorKit.AbstractTensorMap{<:Any, S, 2, 4} where S<:TensorKit.ElementarySpace)`
