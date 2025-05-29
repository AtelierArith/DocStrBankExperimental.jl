```
convertvalue(T, x::LabeledArray)
```

Convert the type of data values contained in `x` to `T`. This method is equivalent to `convert(AbstractArray{LabeledValue{T, K}, N}}, x)`.
