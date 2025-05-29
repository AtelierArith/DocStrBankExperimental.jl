```
description(x) -> String
```

好きなことを書ける説明。

---

```
description(x::AbstractProperty) -> String
```

プロパティ `x` の説明を返します。

## 例

```jldoctest
julia> using FieldProperties

julia> description(description)
"好きなことを書ける説明。\n"
```
