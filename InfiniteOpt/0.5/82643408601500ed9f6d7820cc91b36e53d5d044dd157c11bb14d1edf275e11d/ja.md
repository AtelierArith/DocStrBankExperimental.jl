```
JuMP.upper_bound(pref::DependentParameterRef)::Number
```

`JuMP.upper_bound` 関数を拡張して、単一の依存無限パラメータに対応させます。無限のドメインに関連する上限を返します。もしそのような上限が明確でない場合はエラーを返します。

**例**

```julia-repl
julia> upper_bound(x[1])
0.0
```
