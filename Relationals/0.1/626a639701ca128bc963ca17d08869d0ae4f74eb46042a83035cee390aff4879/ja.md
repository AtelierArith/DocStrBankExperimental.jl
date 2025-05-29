```
destroy(T::Type{<:Relational}, key::Union{Int,UUID}; kwargs...)
```

ユニークキー（Int型の:idまたはUUID型の:uuid）に一致するレコードを削除します。

## 例

```julia
# 最初のUserレコードを取得します。
julia> destroy(Manufacturer, 1)
```
