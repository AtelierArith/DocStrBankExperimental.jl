```
onfinal!(re::RE, a::Union{Symbol, Vector{Symbol}}) -> re
```

正規表現 `re` の最後のバイトが発生する際にアクション `a` を設定します。もし `re` に明確な最終バイトがない場合、例えば `re"a(bc)*"` のように、常に追加できる "bc" がある場合、最終アクションを設定した後に正規表現をコンパイルするとエラーが発生します。ベクターを渡すことで複数のアクションが設定された場合、アクションは順番に実行されます。

参照: [`onenter!`](@ref), [`onall!`](@ref), [`onexit!`](@ref)

# 例

```julia
julia> regex = re"ab?c";

julia> regex2 = onfinal!(regex, :entering_last_byte);

julia> regex === regex2
true

julia> compile(onfinal!(re"ab?c*", :does_not_work))
ERROR: [...]
```
