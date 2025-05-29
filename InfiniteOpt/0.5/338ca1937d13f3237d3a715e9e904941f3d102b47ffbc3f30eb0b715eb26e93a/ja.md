```
used_by_measure(pref::Union{IndependentParameterRef, FiniteParameterRef})::Bool
```

`pref` が測定に使用されている場合は true を返し、そうでない場合は false を返します。

**例**

```julia-repl
julia> used_by_measure(t)
false
```
