```
delete_supports(prefs::AbstractArray{<:DependentParameterRef};
                [label::Type{<:AbstractSupportLabel} = All])::Nothing
```

`prefs`のサポートポイントを削除します。パラメータのいずれかが測定に使用されている場合や、すべてが同じ依存パラメータのセットに属していない場合はエラーが発生します。`label != All`の場合、そのラベルは削除され、そのラベルのみを含むサポートも削除されます。

**例**

```julia-repl
julia> delete_supports(w)

```
