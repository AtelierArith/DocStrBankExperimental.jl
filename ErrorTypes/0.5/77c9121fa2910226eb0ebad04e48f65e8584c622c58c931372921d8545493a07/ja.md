```
unwrap(x::Result)
```

`x` が関連するエラー型の場合、エラーをスローします。そうでなければ、含まれている結果型を返します。

参照: [`unwrap_error`](@ref), [`@unwrap_or`](@ref)

# 例

```jldoctest
julia> unwrap(some(Any[]))
Any[]

julia> unwrap(none(Int))
ERROR: unwrap on unexpected type
[...]

julia> unwrap(Result{String, Int32}(Ok("Lin Wei")))
"Lin Wei"
```
