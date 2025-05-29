```
Box(low::Number, high::Number, shape::Union{Tuple, Array{<:Integer, 1}}, dtype::Union{DataType, Nothing}=nothing; seed::Int=42)
```

R^nのボックス、すなわち各座標が制約されています。

2種類の有効な入力:     Box(-1.0, 1.0, (3,4)) # lowとhighはスカラーで、shapeが提供されています     Box([-1.0,-2.0], [2.0,4.0]) # lowとhighは同じ形状の配列です
