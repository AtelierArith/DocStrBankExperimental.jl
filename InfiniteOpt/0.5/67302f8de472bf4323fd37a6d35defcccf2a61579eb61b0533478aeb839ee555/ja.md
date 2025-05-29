```
delete_supports(pref::IndependentParameterRef; 
                [label::Type{<:AbstractSupportLabel} = All])::Nothing
```

`pref`のサポートポイントを削除します。`label != All`の場合、`label`とそれにのみ依存するサポートを削除します。

**例**

```julia-repl
julia> delete_supports(t)

julia> supports(t)
ERROR: Parameter t does not have supports.
```
