```
function from_df(df::Array{T,2}, name_list::Vector{String})::GeneralNode{T, Int64} where T<:Real
```

この関数は隣接行列と名前のベクトルを受け取り、それを木に変換します。チェックは行われません。

木の根ノードを返します。

  * `df` : エッジの重みを持つ行列
  * `name_list` : 行列の列インデックスに一致する名前のリスト
