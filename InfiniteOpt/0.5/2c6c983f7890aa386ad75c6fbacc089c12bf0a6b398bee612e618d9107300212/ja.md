```
used_by_constraint(pref::DependentParameterRef)::Bool
```

依存する無限パラメータ `pref` が制約によって使用されているかどうかを示す `Bool` を返します。

**例**

```julia-repl
julia> used_by_constraint(pref)
false
```
