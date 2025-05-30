```
InexactError(name::Symbol, T, val)
```

`val`を型`T`に正確に変換できません `name`関数のメソッド内で。

# 例

```jldoctest
julia> convert(Float64, 1+2im)
ERROR: InexactError: Float64(1 + 2im)
Stacktrace:
[...]
```
