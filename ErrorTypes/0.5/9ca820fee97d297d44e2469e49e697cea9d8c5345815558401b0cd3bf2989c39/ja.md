```
is_error(x::Result)
```

`x`がエラー値を含んでいるかどうかを確認します。

参照: [`Result`](@ref), [`Option`](@ref)

# 例

```jldoctest
julia> is_error(none(Int)), is_error(some(5))
(true, false)
```
