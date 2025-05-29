```
get_status_message(s::Status)::String
```

量子計算の`Status`に関連付けられたメッセージを返します。

# 例

```jldoctest
julia> get_status_message(Status(type = "FAILED", message = "something failed"))
"something failed"

```
