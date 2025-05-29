```
supports(cref::InfOptConstraintRef; 
         [label::Type{<:AbstractSupportLabel} = PublicLabel,
         ndarray::Bool = false,
         kwargs...])
```

`cref`に関連付けられたサポートを返します。`cref`が`optimizer_model`に保存されている制約マッピングに関連付けられていない場合はエラーになります。

キーワード引数`label`と`ndarray`は`TranscriptionOpt`が使用するものであり、`kwargs`はユーザー拡張が`constraint_supports`の実装に従って使用する可能性のある追加の引数を示します。そのような拡張が書かれていない場合はエラーになります。

デフォルトでは、公開サポートのみが返され、完全なセットは`label = All`を介してアクセスできます。さらに、無限制約のサポートはリストとして返されます。ただし、制約が複数の無限パラメータ依存性を持つ場合は、`ndarray = true`を使用することでn次元配列を取得でき、便利です。

**例**

```julia-repl
julia> supports(cref)
2-element Array{Tuple{Float64},1}:
 (0.0,)
 (1.0,)
```
