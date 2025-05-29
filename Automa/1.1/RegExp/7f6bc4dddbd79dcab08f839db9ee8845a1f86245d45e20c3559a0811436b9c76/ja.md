```
onexit!(re::RE, a::Union{Symbol, Vector{Symbol}}) -> re
```

正規表現 `re` の一部でなくなる最初のバイトを読み取るとき、または予期されるファイルの終わりに遭遇したときに、アクション `a` を実行するように設定します。ベクターを渡すことで複数のアクションが設定されている場合は、アクションを順番に実行します。

参照: [`onenter!`](@ref), [`onall!`](@ref), [`onfinal!`](@ref)

# 例

```julia
julia> regex = re"ab?c*";

julia> regex2 = onexit!(regex, :exiting_regex);

julia> regex === regex2
true
```
