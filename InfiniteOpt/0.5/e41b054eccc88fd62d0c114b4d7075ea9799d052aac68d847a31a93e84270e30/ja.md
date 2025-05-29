```
num_supports(pref::DependentParameterRef; 
             [label::Type{<:AbstractSupportLabel} = PublicLabel])::Int
```

単一の依存無限パラメータ `pref` に関連付けられたサポートポイントの数を返します。`label` を指定することで、特定のサポートのみをカウントします。デフォルトでは、公開サポートの数のみが返されますが、`label == All` を指定することで全てのサポートの数を取得できます。

**例**

```julia-repl
julia> num_supports(x[1])
2

julia> num_supports(x[1], label = MCSample)
0
```
