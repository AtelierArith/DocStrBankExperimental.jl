```
supports(prefs::AbstractArray{<:DependentParameterRef};
         [label::Type{<:AbstractSupportLabel} = PublicLabel]
         )::Union{Vector{<:AbstractArray{<:Real}}, Array{Float64, 2}}
```

`prefs`に関連付けられたサポートポイントを返します。すべての無限依存パラメータが同じオブジェクトからでない場合はエラーになります。`prefs`が`Vector`の場合は行列が返され、それ以外の場合は各配列が`prefs`の形式に一致するサポートポイントのベクトルが返されます。`label`を介してサポートのサブセットを返すことができ、`label`に関連付けられたサポートのみを返します。デフォルトでは公開サポートのみが与えられますが、`label == All`を使用することで完全なセットが取得できます。

**例**

```julia-repl
julia> supports(x) # 列はサポートです
2×2 Array{Float64,2}:
 0.0  1.0
 0.0  1.0
```
