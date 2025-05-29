```
optimizer_model_expression(expr::JuMP.AbstractJuMPScalar; 
                           [label::Type{<:AbstractSupportLabel} = PublicLabel,
                           ndarray::Bool = false, 
                           kwargs...])
```

`expr` に対応する最適化モデルに格納されている再定式化式を返します。また、最適化モデルにそのような式が見つからない場合（つまり、基になる変数の1つ以上が転写されていない場合）にはエラーを返します。

キーワード引数 `label` と `ndarray` は `TranscriptionOpt` が使用するものであり、`kwargs` はユーザー拡張が [`optimizer_model_expression`](@ref) の実装に従って使用する追加のものを示します。そのような拡張が書かれていない場合はエラーを返します。

デフォルトでは、公開サポートに関連付けられた式のみが返され、完全なセットは `label = All` を介してアクセスできます。さらに、無限の式はそのサポートに対応するリストとして返されます。ただし、式が複数の無限パラメータ依存性を持つ場合に便利な `ndarray = true` を使用すると、n次元配列を取得できます。対応するサポートは、同じキーワード引数を使用して `supports` を介して取得されます。

**例**

```julia-repl
julia> optimizer_model_expression(my_expr) # 有限式
x(support: 1) - y
```
