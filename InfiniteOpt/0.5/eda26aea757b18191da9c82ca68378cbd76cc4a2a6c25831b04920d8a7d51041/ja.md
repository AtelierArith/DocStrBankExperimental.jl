```
used_by_constraint(pref::Union{IndependentParameterRef, FiniteParameterRef})::Bool
```

`pref` が制約によって使用されている場合は true を返し、そうでない場合は false を返します。

**例**

```julia-repl
julia> used_by_constraint(t)
true
```
