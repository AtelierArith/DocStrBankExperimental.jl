```
onall!(re::RE, a::Union{Symbol, Vector{Symbol}}) -> re
```

正規表現 `re` の任意のバイト部分を読み取るときに、アクション `a` を実行するように設定します。ベクターを渡して複数のアクションを設定した場合は、アクションを順番に実行します。

参照: [`onenter!`](@ref), [`onexit!`](@ref), [`onfinal!`](@ref)

# 例

```julia
julia> regex = re"ab?c*";

julia> regex2 = onall!(regex, :reading_re_byte);

julia> regex === regex2
true
```
