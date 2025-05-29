```
used_by_infinite_variable(pref::DependentParameterRef)::Bool
```

依存する無限パラメータ `pref` が無限変数によって使用されているかどうかを示す `Bool` を返します。

**例**

```julia-repl
julia> used_by_infinite_variable(pref)
true
```
