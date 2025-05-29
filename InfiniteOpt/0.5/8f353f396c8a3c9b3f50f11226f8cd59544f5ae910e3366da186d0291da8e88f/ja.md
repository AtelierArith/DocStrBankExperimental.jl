```
JuMP.lower_bound(pref::IndependentParameterRef)::Real
```

`JuMP.lower_bound` 関数を無限のパラメータに対応するように拡張します。無限の領域に関連する下限を返します。そのような下限が明確でない場合はエラーを返します。

**例**

```julia-repl
julia> lower_bound(t)
0.0
```
