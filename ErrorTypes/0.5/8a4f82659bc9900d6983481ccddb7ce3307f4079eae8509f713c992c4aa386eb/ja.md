```
unwrap_error(x::Result)
```

`x`が`Err`を含む場合、`Err`の内容を返します。そうでなければ、エラーをスローします。

参照: [`unwrap`](@ref), [`expect_error`](@ref)

# 例

```jldoctest
julia> unwrap_error(some(3))
ERROR: unwrap on unexpected type
[...]

julia> unwrap_error(none(String)) === nothing
true

julia> unwrap_error(Result{Int, String}(Err("some error")))
"some error"
```
