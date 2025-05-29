```
unwrap_or_else(f, x::Result)
```

もし `x` がエラー値であれば、`f(unwrap_error(x))` を返します。そうでなければ、`x` をアンラップしてその内容を返します。

参照: [`unwrap_error_or_else`](@ref), [`unwrap_or`](@ref)

# 例

```jldoctest
julia> unwrap_or_else(isnothing, some(3))
3

julia> unwrap_or_else(println, none(Int))
nothing

julia> unwrap_or_else(ncodeunits, Result{Int, String}(Err("my_error")))
8
```
