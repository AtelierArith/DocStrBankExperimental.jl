```
execute_on_input(tab::SymbolTable, expr::Any, input::Vector{T})::Vector{<:Any} where T <: Dict{Symbol, <:Any}
```

[`execute_on_input`](@ref)のラッパーで、配列として与えられたすべての入力を実行します。

# 引数

  * `tab::SymbolTable`: 事前定義されたシンボルとそれに関連付けられた値または関数を含むシンボルテーブル。
  * `expr::Any`: 各入力辞書に対して評価される式。
  * `inputs::Vector{T}`: 各辞書が式の評価のための個別の入力セットとして機能する辞書のベクター。

# 戻り値

  * `Vector{<:Any}`: 各入力辞書に対して式を評価した結果を含むベクター。
