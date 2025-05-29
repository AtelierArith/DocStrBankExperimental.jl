```
transcription_variable(model::JuMP.Model,
    vref::InfiniteOpt.GeneralVariableRef;
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
     ndarray::Bool = false])
```

`vref`に対応する転写変数参照を返します。転写変数が見つからない場合はエラーになります。また、次の構文を使用してクエリを実行できます。

```julia
transcription_variable(vref::InfiniteOpt.GeneralVariableRef; 
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
     ndarray::Bool = false])
```

無限モデルに構築された転写モデルが含まれている場合。デフォルトでは、このメソッドは公開サポートに関連付けられた転写変数のみを返します。すべての変数は、`label = All`を設定することで返すことができます。

`vref`が無限であり、`ndarray = true`の場合、ユニークなオブジェクト番号を持つ無限パラメータに従ってn次元配列が返されます。この場合、`label`はラベルを使用する変数サポートの交差点を検索するために使用されます。これは、和集合を考慮するデフォルトの動作とは異なります。

**例**

```julia-repl
julia> transcription_variable(trans_model, infvar)
2-element Array{VariableRef,1}:
 infvar(support: 1)
 infvar(support: 2)

julia> transcription_variable(trans_model, hdvar)
hdvar

julia> transcription_variable(infvar)
2-element Array{VariableRef,1}:
 infvar(support: 1)
 infvar(support: 2)

julia> transcription_variable(hdvar)
hdvar
```
