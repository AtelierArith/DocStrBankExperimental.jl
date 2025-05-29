```
unwrap_or(x::Result, v)
```

`x`がエラー値の場合、`v`を返します。そうでなければ、`x`をアンラップしてその内容を返します。

参照: [`unwrap`](@ref), [`@unwrap_or`](@ref)

# 例:

```jldoctest
julia> unwrap_or(some(5), 9)
5

julia> unwrap_or(none(Float32), "something else")
"something else"

julia> unwrap_or(Result{Int8, Vector}(Err([])), 0x01)
0x01
```
