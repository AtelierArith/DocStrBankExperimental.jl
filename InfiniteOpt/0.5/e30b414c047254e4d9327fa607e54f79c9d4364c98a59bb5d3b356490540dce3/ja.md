```
JuMP.set_upper_bound(pref::IndependentParameterRef, lower::Real)::Nothing
```

`JuMP.set_upper_bound` 関数を無限パラメータに対応するように拡張します。無限の範囲の上限は、IntervalDomain の場合にのみ更新されます。それ以外の場合はエラーになります。ユーザー定義の無限範囲を持つ拡張は、適切であれば `JuMP.set_upper_bound(domain::NewType, upper::Number)` を拡張する必要があります。

**例**

```julia-repl
julia> set_upper_bound(t, 2)

julia> upper_bound(t)
2.0
```
