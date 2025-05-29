```
JuMP.has_upper_bound(pref::DependentParameterRef)::Bool
```

`JuMP.has_upper_bound` 関数を拡張して、単一の依存無限パラメータに対応させます。`pref` に関連付けられたドメインに定義された上限がある場合、または上限を見つけることができる場合は true を返します。ユーザー定義のスカラー無限ドメインタイプを使用した拡張は、`JuMP.has_upper_bound(domain::NewType)` を拡張する必要があります。

**例**

```julia-repl
julia> has_upper_bound(x[1])
true
```
