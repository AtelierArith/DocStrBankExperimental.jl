```
NumPyArray(a::AbstractArray, [revdims::Bool])
```

Convert an AbstractArray where `isapplicable(strides, a)` is `true` to a NumPy array. The AbstractArray must either be mutable or have a mutable parent. Optionally, transpose the dimensions of the array if `revdims` is `true`.
