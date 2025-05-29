```
transcription_expression(
    model::JuMP.Model,
    expr::JuMP.AbstractJuMPScalar;
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

`expr` に対応する転写された式を返します。`expr` を転写できない場合はエラーが発生します。また、次の構文を使用してクエリを実行できます：

```julia
transcription_expression(expr::JuMP.AbstractJuMPScalar;
                         [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
                         ndarray::Bool = false])
```

無限モデルに構築された転写モデルが含まれている場合。このメソッドはデフォルトで、公開サポートに関連する転写された式のみを返します。すべての式は、`label = All` を設定することで返すことができます。

`expr` が無限であり、`ndarray = true` の場合、ユニークなオブジェクト番号を持つ無限パラメータに従って n 次元配列が返されます。この場合、`label` はラベルを使用するサポートの交差点を検索するために使用されます。これは、和集合を考慮するデフォルトの動作とは異なります。

**例**

```julia-repl
julia> transcription_expression(trans_model, my_expr)
x(support: 1) - y

julia> transcription_expression(my_expr)
x(support: 1) - y
```
