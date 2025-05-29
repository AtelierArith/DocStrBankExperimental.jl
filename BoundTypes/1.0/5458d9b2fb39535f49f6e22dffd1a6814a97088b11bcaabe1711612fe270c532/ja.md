```
bound_type(x) -> type
```

`x`の内部オブジェクトの型を返します。

## 例

```jldoctest
julia> bound_type(NumberPositive{Float64}(1.0))
Float64

julia> bound_type(NumberLess{NumberGreater{Int64,2},8}(6))
Int64
```
