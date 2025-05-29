```
JuMP.set_name(cref::InfOptConstraintRef, name::String)::Nothing
```

`JuMP.set_name`を拡張して、制約`cref`の名前を指定します。

**例**

```julia-repl
julia> set_name(cref, "new_name")

julia> name(cref)
"new_name"
```
