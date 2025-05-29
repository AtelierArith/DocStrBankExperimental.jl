```
unwrap_error_or(f, x::Result
```

`x`がエラーの場合はラップされたエラー値を返し、そうでなければ`f(unwrap(x))`を返します。

関連情報: [`@unwrap_error_or`](@ref), [`unwrap_or_else`](@ref)

# 例

```jldoctest
julia> unwrap_error_or_else(ncodeunits, some("abc"))
3

julia> unwrap_error_or_else(ncodeunits, none(String)) === nothing
true

julia> unwrap_error_or_else(n -> n + 1, Result{Int, String}(Err("abc")))
"abc"
```
