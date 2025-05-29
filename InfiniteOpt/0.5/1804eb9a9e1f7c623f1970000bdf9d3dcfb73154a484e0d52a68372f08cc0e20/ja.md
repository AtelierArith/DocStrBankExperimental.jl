```
JuMP.set_lower_bound(pref::IndependentParameterRef, lower::Real)::Nothing
```

`JuMP.set_lower_bound` 関数を無限パラメータに対応するように拡張します。この操作がサポートされている場合、無限ドメインの下限を更新します。この機能を利用しようとする拡張は `JuMP.set_lower_bound(domain::NewType, lower::Number)` を拡張する必要があります。

**例**

```julia-repl
julia> set_lower_bound(t, -1)

julia> lower_bound(t)
-1.0
```
