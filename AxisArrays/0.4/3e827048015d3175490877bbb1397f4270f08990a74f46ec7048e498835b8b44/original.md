```
axisnames(A::AxisArray)           -> (Symbol...)
axisnames(::Type{AxisArray{...}}) -> (Symbol...)
axisnames(ax::Axis...)            -> (Symbol...)
axisnames(::Type{Axis{...}}...)   -> (Symbol...)
```

Returns the axis names of an AxisArray or list of Axises as a tuple of Symbols.
