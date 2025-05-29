```
unwrap_error_or(x::Result, v)
```

`unwrap_or`のように、エラーをアンラップします。

参照: [`unwrap_or`](@ref)

# 例

```jldoctest
julia> unwrap_error_or(Result{Int, String}(Err("abc")), 19)
"abc"

julia> unwrap_error_or(none(String), "error") === nothing
true

julia> unwrap_error_or(some([1, 2, 3]), Int32[])
Int32[]
```
