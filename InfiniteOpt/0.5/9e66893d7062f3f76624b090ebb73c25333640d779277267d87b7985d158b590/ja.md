```
JuMP.has_upper_bound(pref::IndependentParameterRef)::Bool
```

`JuMP.has_upper_bound` 関数を無限パラメータに対応するように拡張します。`pref` に関連付けられたドメインに定義された上限がある場合、または上限を見つけることができる場合は true を返します。ユーザー定義のドメインを持つ拡張は `JuMP.has_upper_bound(domain::NewType)` を拡張する必要があります。

**例**

```julia-repl
julia> has_upper_bound(t)
true
```
