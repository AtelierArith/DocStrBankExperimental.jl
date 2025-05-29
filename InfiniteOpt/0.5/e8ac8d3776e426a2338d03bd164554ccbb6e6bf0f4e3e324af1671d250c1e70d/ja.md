```
optimizer_model_variable(vref::GeneralVariableRef; 
                         [label::Type{<:AbstractSupportLabel} = PublicLabel, 
                         ndarray::Bool = false,
                         kwargs...])
```

最適化モデルに格納されている再定式化変数を返します。これらは `vref` に対応しています。また、最適化モデルにそのような変数が見つからない場合はエラーが発生します。

キーワード引数 `label` と `ndarray` は `TranscriptionOpt` が使用するものであり、`kwargs` はユーザー拡張がその実装に従って使用する追加の引数を示します。もしそのような拡張が書かれていない場合はエラーが発生します。

デフォルトでは、公開サポートに関連付けられた変数のみが返されます。全セットには `label = All` を使用してアクセスできます。さらに、無限変数はそのサポートに対応するリストとして返されます。ただし、変数が複数の無限パラメータ依存性を持つ場合は、`ndarray = true` を使用して n 次元配列を取得できます。対応するサポートは、同じキーワード引数を使用して `supports` を介して取得されます。

**例**

```julia-repl
julia> optimizer_model_variable(x) # 無限変数
2-element Array{VariableRef,1}:
 x(support: 1)
 x(support: 2)

julia> optimizer_model_variable(z) # 有限変数
z
```
