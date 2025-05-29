```
axisnames(A::AxisArray)           -> (Symbol...)
axisnames(::Type{AxisArray{...}}) -> (Symbol...)
axisnames(ax::Axis...)            -> (Symbol...)
axisnames(::Type{Axis{...}}...)   -> (Symbol...)
```

AxisArrayまたはAxisのリストの軸名をシンボルのタプルとして返します。
