```
none(::Type)::Option{T}
```

`Option{T}`のエラー値を構築します。

参照: [`Option`](@ref)

# 例

```jldoctest
julia> none(String) === Option{String}(Err(nothing))
true

julia> none(Char) isa Option{Char}
true

julia> is_error(none(Char))
true

julia> convert(Option{Vector}, none) === none(Vector)
true
```
