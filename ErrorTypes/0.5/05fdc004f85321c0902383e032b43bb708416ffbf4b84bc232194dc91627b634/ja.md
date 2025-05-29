```
map_or(f, x::Result, v)
```

`x` が結果値であれば、`f(unwrap(x))` を返します。そうでなければ、`v` を返します。

参照: [`unwrap_or`](@ref), [`and_then`](@ref)

# 例

```jldoctest
julia> map_or(isodd, some(9), nothing)
true

julia> map_or(isodd, none(Int), nothing) === nothing
true

julia> map_or(ncodeunits, none(String), 0)
0
```
