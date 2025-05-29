```
JuMP.upper_bound(pref::IndependentParameterRef)::Real
```

`JuMP.upper_bound` 関数を拡張して無限のパラメータに対応させます。無限のドメインに関連付けられた上限を返します。もしそのような上限が明確でない場合はエラーを返します。ユーザー定義のドメインタイプを使用した拡張は、必要に応じて `JuMP.has_upper_bound(domain::NewType)` と `JuMP.upper_bound(domain::NewType)` を拡張する必要があります。

**例**

```julia-repl
julia> upper_bound(t)
1.0
```
