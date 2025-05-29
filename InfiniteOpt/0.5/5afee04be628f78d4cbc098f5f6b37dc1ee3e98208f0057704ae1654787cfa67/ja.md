```
num_supports(pref::IndependentParameterRef; 
             [label::Type{<:AbstractSupportLabel} = PublicLabel])::Int
```

`pref`に関連付けられたサポートポイントの数を返します。デフォルトでは、公開サポートの数のみがカウントされます。`label = All`を設定することで、全体の数を決定できます。さらに、`label`を満たすラベルの数は[`AbstractSupportLabel`](@ref)を使用して取得されます。

**例**

```julia-repl
julia> num_supports(t)
2
```
