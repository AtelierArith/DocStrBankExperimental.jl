```
used_by_derivative(pref::DependentParameterRef)::Bool
```

依存する無限パラメータ `pref` が導関数によって使用されているかどうかを示す `Bool` を返します。

**例**

```julia-repl
julia> used_by_derivative(pref)
false
```
