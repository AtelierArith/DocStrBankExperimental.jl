```
ncatt_get(f::NCfiles, key)
ncatt_put(f::AbstractString, attrib = Dict())
ncatt_del(f::AbstractString, keys::Vector{<:AbstractString})
```

グローバル属性を追加または削除します。
