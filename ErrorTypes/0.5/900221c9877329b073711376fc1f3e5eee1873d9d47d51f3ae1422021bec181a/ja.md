```
Option{T}
```

`Result{T, Nothing}`のエイリアス。`Result`のエラータイプが情報を保存する必要がない場合に便利です。値インスタンスは`some(x)`で、エラーインスタンスは`none(::Type)`で構築します。

参照: [`Result`](@ref)

# 例

```jldoctest
julia> some(4) isa Option{Int}
true

julia> is_error(some(4))
false

julia> none(String) isa Option{String} && is_error(none(String))
true
```
