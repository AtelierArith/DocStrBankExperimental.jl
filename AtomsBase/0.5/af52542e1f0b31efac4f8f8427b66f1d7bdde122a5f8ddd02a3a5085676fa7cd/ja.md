```
velocity(sys::AbstractSystem, i)
```

`i::Integer` の場合は速度ベクトルを返し、`i` が整数のベクトルまたは `:` の場合は速度のベクトルを返します。戻り値の型は、各要素が `<:Unitful.Velocity` の `D` 要素を含むベクトルのベクトルである必要があります。関数の戻り値は `missing` である可能性があります。
