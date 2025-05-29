```
axes(A::AxisArray) -> (Axis...)
axes(A::AxisArray, ax::Axis) -> Axis
axes(A::AxisArray, dim::Int) -> Axis
```

AxisArrayの軸ベクトルのタプルを返します。特定の`Axis`が指定されている場合、その軸ベクトルのみが返されます。単一の軸ベクトルを抽出する際には、`axes(A, Axis{1})`が型安定であり、`axes(A)[1]`よりもパフォーマンスが向上します。

`Axis`情報のないAbstractArrayに対しては、`axes`はデフォルトの軸を返します。つまり、`AxisArray(A)`によって生成される軸です。
