```
NumPyArray(a::AbstractArray, [revdims::Bool])
```

`isapplicable(strides, a)` が `true` の AbstractArray を NumPy 配列に変換します。AbstractArray は可変であるか、可変の親を持っている必要があります。オプションで、`revdims` が `true` の場合は配列の次元を転置します。
