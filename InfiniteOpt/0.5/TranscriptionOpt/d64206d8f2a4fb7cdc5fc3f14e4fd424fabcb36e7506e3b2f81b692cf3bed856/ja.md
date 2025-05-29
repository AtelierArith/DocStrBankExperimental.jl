```
transcription_constraint(model::JuMP.Model,
    cref::InfiniteOpt.InfOptConstraintRef;
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

`cref` に対応する転写された制約参照を返します。`cref` が転写されていない場合はエラーになります。また、次の構文を使用してクエリできます：

```julia
transcription_constraint(cref::InfiniteOpt.InfOptConstraintRef;
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

無限モデルに構築された転写モデルが含まれている場合。デフォルトでは、このメソッドは公開サポートに関連付けられた転写された制約のみを返します。すべての制約は、`label = All` を設定することで返すことができます。

`cref` が無限であり、`ndarray = true` の場合、ユニークなオブジェクト番号を持つ無限パラメータに従って n 次元配列が返されます。この場合、`label` はラベルを使用するサポートの交差点を検索するために使用されます。これは、和集合を考慮するデフォルトの動作とは異なります。

**例**

```julia-repl
julia> transcription_constraint(trans_model, fin_con)
fin_con : x(support: 1) - y <= 3.0

julia> transcription_constraint(fin_con)
fin_con : x(support: 1) - y <= 3.0
```
