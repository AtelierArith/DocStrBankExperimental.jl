```
    reference_domain(EG::Type{<:AbstractElementGeometry}, T::Type{<:Real} = Float64; scale = [1,1,1], shift = [0,0,0]) -> ExtendableGrid{T,Int32}
```

指定された要素幾何の参照ドメインのためにExtendableGrid{T,Int32}を生成します。スケールとシフトを使用することで、座標を操作できます。
