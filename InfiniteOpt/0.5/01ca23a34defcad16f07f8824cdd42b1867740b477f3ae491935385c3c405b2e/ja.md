```
used_by_parameter_function(pref::IndependentParameterRef)::Bool
```

`pref` が無限パラメータ関数で使用されている場合は true を返し、そうでない場合は false を返します。

**例**

```julia-repl
julia> used_by_parameter_function(t)
false
```
