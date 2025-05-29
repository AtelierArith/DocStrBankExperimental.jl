```
used_by_parameter_function(pref::DependentParameterRef)::Bool
```

依存する無限パラメータ `pref` が無限パラメータ関数によって使用されているかどうかを示す `Bool` を返します。

**例**

```julia-repl
julia> used_by_parameter_function(pref)
true
```
