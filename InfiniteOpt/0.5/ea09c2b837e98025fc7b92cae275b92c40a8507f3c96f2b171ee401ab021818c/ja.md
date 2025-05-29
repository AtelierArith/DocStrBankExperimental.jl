```
supports(expr::JuMP.AbstractJuMPScalar; 
         [label::Type{<:AbstractSupportLabel} = PublicLabel,
         ndarray::Bool = false,
         kwargs...])
```

`expr`に関連付けられたサポートを返します。`expr`が`optimizer_model`に保存されている制約マッピングに関連付けられていない場合はエラーになります。

キーワード引数`label`と`ndarray`は`TranscriptionOpt`が使用するものであり、`kwargs`はユーザー拡張が`expression_supports`の実装に従って使用する可能性のある追加の引数を示します。そのような拡張が書かれていない場合はエラーになります。

デフォルトでは、公開サポートのみが返され、完全なセットは`label = All`を介してアクセスできます。さらに、無限の表現のサポートはリストとして返されます。ただし、`ndarray = true`を使用するとn次元配列を取得でき、これは表現が複数の無限パラメータ依存性を持つ場合に便利です。

**例**

```julia-repl
julia> supports(cref)
2-element Array{Tuple{Float64},1}:
 (0.0,)
 (1.0,)
```
