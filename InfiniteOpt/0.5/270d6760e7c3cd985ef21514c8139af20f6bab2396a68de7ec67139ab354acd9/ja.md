```
JuMP.lower_bound(pref::DependentParameterRef)::Number
```

`JuMP.lower_bound` 関数を拡張して、単一の依存無限パラメータに対応します。無限のドメインに関連付けられた下限を返します。そのような下限が明確でない場合はエラーを返します。

**例**

```julia-repl
julia> lower_bound(x[1])
0.0
```
