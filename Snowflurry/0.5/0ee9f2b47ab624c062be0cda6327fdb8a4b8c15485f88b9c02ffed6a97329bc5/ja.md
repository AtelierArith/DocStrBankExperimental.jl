```
get_status_type(s::Status)::String
```

量子計算の`Status`に関連付けられたタイプを返します。

可能な`type`文字列の詳細については、[`Status`](@ref)を参照してください。

# 例

```jldoctest
julia> get_status_type(Status(type = "SUCCEEDED"))
"SUCCEEDED"

```
