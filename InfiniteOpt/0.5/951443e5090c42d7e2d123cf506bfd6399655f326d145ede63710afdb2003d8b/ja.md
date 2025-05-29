```
set_supports(pref::IndependentParameterRef, supports::Vector{<:Real};
             [force::Bool = false,
             label::Type{<:AbstractSupportLabel} = UserDefined]
             )::Nothing
```

`pref`のサポートポイントを指定します。サポートが無限の領域に関連する境界を違反する場合はエラーが発生します。ポイントが一意でない場合は警告が表示されます。`force`が指定されている場合は既存のサポートを上書きしますが、そうでない場合は既存のサポートがあるとエラーになります。

**例**

```julia-repl
julia> set_supports(t, [0, 1])

julia> supports(t)
2-element Array{Int64,1}:
 0
 1
```
