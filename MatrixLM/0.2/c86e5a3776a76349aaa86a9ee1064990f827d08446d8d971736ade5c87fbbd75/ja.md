```
contr(df::DataFrames.DataFrame, cVars::AbstractArray{Symbol,1}, 
      cTypes::AbstractArray{String,1}=repeat(["treat"], inner=length(cVars)), 
      trtRefs::AbstractArray= repeat([nothing], inner=length(cVars)))
```

DataFrame内のカテゴリ変数を指定されたコントラストタイプに変換します。他のすべての変数はそのまま残されます。

# 引数

  * `df::DataFrames.DataFrame`: 変数のDataFrame
  * `cVar::Symbol`: 変換されるdf内のカテゴリ変数のシンボル
  * `cTypes::AbstractArray{String,1}`: `cVars`と同じ長さの文字列の1次元配列で、使用するコントラストのタイプを示します。デフォルトでは、`cVars`内のすべての変数に対して処置コントラスト（"treat"）が使用されます。他のオプションには、合計コントラストのための"sum"、切片のない処置コントラストのための"noint"、および切片のない合計コントラストのための"sumnoint"が含まれます。"treat" `cTypes`の場合、`trtRefs`を使用して参照処置として使用するレベルを指定することもできます。
  * `trtRefs::AbstractArray`: オプションの1次元配列で、`cVars`と同じ長さの文字列で、処置コントラストの参照として使用するレベルを指定します。デフォルトでは、`cVars`内のすべての変数に対してnothingです。

# 値

元のDataFrameと同じ変数を持つDataFrameですが、カテゴリ変数はダミーコントラストに変換されています。

# 一部の注意事項

`cVars`が空のシンボルのみで構成されている場合、すなわち`cVars=[Symbol()]`の場合、これは関数に対してコントラストを作成しないことを示します。元のDataFrameが返されます。
