```
used_by_infinite_variable(pref::IndependentParameterRef)::Bool
```

`pref` が無限変数によって使用されている場合は true を返し、そうでない場合は false を返します。

**例**

```julia-repl
julia> used_by_infinite_variable(t)
true
```
