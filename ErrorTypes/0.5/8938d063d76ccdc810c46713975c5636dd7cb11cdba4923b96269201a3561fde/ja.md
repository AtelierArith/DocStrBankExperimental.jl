```
expect_error(x::Result, s::AbstractString)
```

もし `x` が `Err` を含む場合、`Err` の内容を返します。そうでなければ、メッセージ `s` でエラーをスローします。

参照: [`unwrap_error`](@ref), [`expect`](@ref)

# 例

```jldoctest
julia> expect_error(none(Int), "expected none") === nothing
true

julia> expect_error(Result{Vector, String}(Err("Mistake!")), "must be error")
"Mistake!"

julia> expect_error(some(3), "must be none")
ERROR: must be none
[...]
```
