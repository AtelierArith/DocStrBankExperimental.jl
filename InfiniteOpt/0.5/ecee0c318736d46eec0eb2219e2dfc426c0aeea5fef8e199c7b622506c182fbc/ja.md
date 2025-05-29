```
supports(vref::DecisionVariableRef; 
         [label::Type{<:AbstractSupportLabel} = PublicLabel, 
         ndarray::Bool = false,
         kwargs...])
```

`vref` に関連付けられたサポートを最適化モデルから返します。[`InfiniteOpt.variable_supports`](@ref) が最適化モデルタイプのために拡張されていない場合や、`vref` が最適化モデルで再定式化されていない場合はエラーが発生します。

キーワード引数 `label` と `ndarray` は `TranscriptionOpt` が使用するものであり、`kwargs` はユーザー拡張が `variable_supports` の実装に従って使用する追加のものを示します。そのような拡張が書かれていない場合はエラーが発生します。

デフォルトでは、公開サポートのみが返され、完全なセットは `label = All` を介してアクセスできます。さらに、無限変数のサポートはリストとして返されます。ただし、`ndarray = true` を使用すると n 次元配列を取得でき、これは変数が複数の無限パラメータ依存性を持つ場合に便利です。

**例**

```julia-repl
julia> supports(vref)
2-element Array{Tuple{Float64},1}:
 (0.0,)
 (1.0,)
```
