```
used_by_derivative(pref::IndependentParameterRef)::Bool
```

`pref` が導関数によって使用されている場合は true を返し、そうでない場合は false を返します。

**例**

```julia-repl
julia> used_by_derivative(t)
false
```
