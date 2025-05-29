```
optimizer_model_constraint(cref::InfOptConstraintRef; 
                           [label::Type{<:AbstractSupportLabel} = PublicLabel, 
                           ndarray::Bool = false,
                           kwargs...])
```

`cref` に対応する最適化モデルに保存されている再定式化制約を返します。最適化モデルにそのような制約が見つからない場合はエラーが発生します。

キーワード引数 `label` と `ndarray` は `TranscriptionOpt` が使用するものであり、`kwargs` はユーザー拡張が [`optimizer_model_constraint`](@ref) の実装に従って使用する可能性のある追加の引数を示します。そのような拡張が書かれていない場合はエラーが発生します。

デフォルトでは、公開サポートに関連付けられた制約のみが返され、完全なセットは `label = All` を介してアクセスできます。さらに、無限制約はそのサポートに対応するリストとして返されます。ただし、制約が複数の無限パラメータ依存性を持つ場合は、`ndarray = true` を使用して n 次元配列を取得できます。対応するサポートは、同じキーワード引数を使用して `supports` を介して取得されます。

**例**

```julia-repl
julia> optimizer_model_constraint(c1) # 有限制約
c1 : x(support: 1) - y <= 3.0
```
