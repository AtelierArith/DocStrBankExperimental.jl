print: 出力フォーマット。DataFrameを返します。

`print(:: ListofStates; verbose :: Bool = true, print_sym :: Union{Nothing,Array{Symbol,1}})`

注意:

  * `verbose`をfalseに設定すると、印刷を避けることができます。
  * `print_sym`がSymbolの配列である場合、指定されたシンボルのみが印刷されます。ただし、

返されるDataFrameにはすべての列が含まれています。

  * DataFrameに関する詳細情報: http://juliadata.github.io/DataFrames.jl

関連情報: add*to*list!, length, ListofStates
