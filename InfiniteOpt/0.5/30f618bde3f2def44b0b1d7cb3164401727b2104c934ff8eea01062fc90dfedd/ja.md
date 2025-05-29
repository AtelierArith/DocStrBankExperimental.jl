```
supports(pref::DependentParameterRef; 
         [label::Type{<:AbstractSupportLabel} = PublicLabel])::Vector{Float64}
```

`pref` に関連付けられたサポートポイントを返します。`label` を使用してサポートのサブセットを返すことができ、`label` に関連付けられたサポートのみを返します。デフォルトでは、公開サポートのみが提供されますが、`label == All` を使用することで完全なセットが取得できます。

**例**

```julia-repl
julia> supports(x[1])
2-element Array{Float64,1}:
 0.0
 1.0
```
