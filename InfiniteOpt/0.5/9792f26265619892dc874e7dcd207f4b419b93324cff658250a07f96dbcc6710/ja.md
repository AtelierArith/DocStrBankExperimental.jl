```
JuMP.has_lower_bound(pref::IndependentParameterRef)::Bool
```

`JuMP.has_lower_bound` 関数を拡張して無限パラメータに対応させます。`pref` に関連付けられたドメインに定義された下限がある場合、または下限を見つけることができる場合は true を返します。ユーザー定義の無限ドメインタイプを使用した拡張は `JuMP.has_lower_bound(domain::NewType)` を拡張する必要があります。

**例**

```julia-repl
julia> has_lower_bound(t)
true
```
