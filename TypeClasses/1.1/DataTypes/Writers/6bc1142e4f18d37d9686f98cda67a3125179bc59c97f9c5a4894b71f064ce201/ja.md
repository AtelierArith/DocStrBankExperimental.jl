```
getaccumulator(writer::Writer)
```

Writer値のアキュムレーターを返します。

## 例

```jldoctest
julia> using TypeClasses

julia> getaccumulator(Writer("example-accumulator"))
"example-accumulator"
```
