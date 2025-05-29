```
JuMP.name(pref::Union{IndependentParameterRef, FiniteParameterRef})::String
```

`JuMP.name` 関数を無限パラメータに対応するように拡張します。`pref` に関連付けられた名前の文字列を返します。

**例**

```julia-repl
julia> name(t)
"t"
```
