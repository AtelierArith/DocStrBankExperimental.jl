```
onenter!(re::RE, a::Union{Symbol, Vector{Symbol}}) -> re
```

正規表現 `re` の最初のバイトを読み取るときに、アクション `a` を実行するように設定します。ベクターを渡して複数のアクションを設定した場合は、アクションを順番に実行します。

参照: [`onexit!`](@ref), [`onall!`](@ref), [`onfinal!`](@ref)

# 例

```julia
julia> regex = re"ab?c*";

julia> regex2 = onenter!(regex, :entering_regex);

julia> regex === regex2
true
```
