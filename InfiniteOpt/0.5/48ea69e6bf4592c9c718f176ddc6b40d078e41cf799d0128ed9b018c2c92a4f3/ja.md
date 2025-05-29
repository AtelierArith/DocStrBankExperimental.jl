```
supports(pref::IndependentParameterRef; 
         [label::Type{<:AbstractSupportLabel} = PublicLabel])::Vector{Float64}
```

`pref` に関連付けられたサポートポイントを返します。サポートがない場合はエラーになります。ユーザーはキーワード引数 `label` を使用して、特定のメソッドによって生成されたサポートポイントのみを照会できます。デフォルトでは、関係するラベルに関係なく、すべての公開サポートポイントが返されます。 `label = All` を設定することで、完全なコレクションが得られます。さらに、`label` を満たすラベルの数は [`AbstractSupportLabel`](@ref) を使用して取得されます。

**例**

```julia-repl
julia> supports(t)
2-element Array{Float64,1}:
 0.0
 1.0
```
