```
show_links(vardom::VariableDomain)
show_links(model::Model, varnamefull::AbstractString)
show_links(io::IO, vardom::VariableDomain)
show_links(io::IO, model::Model, varnamefull::AbstractString)
```

この[`VariableDomain`](@ref)にリンクされているすべての[`VariableReaction`](@ref)を表示します。

`varnamefull`は"<domain name>.<variable name>"の形式である必要があります。

リンクされた変数は"<domain name>.<reaction name>.<method name>.<local name>"として表示されます。
