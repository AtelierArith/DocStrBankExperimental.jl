```
JuMP.set_name(fref::ParameterFunctionRef, name::String)::Nothing
```

`JuMP.set_name`を拡張して、パラメータ関数の名前を設定します。

**例**

```julia-repl
julia> set_name(fref, "func_name")

julia> name(fref)
"func_name"
```
