```
セル
```

セルのデータ型。

# フィールド

  * `name::String`: セルの名前を格納します。
  * `lattice::Lattice{<:Real}`: 格子に関するメタデータを格納します。
  * `atoms::Array{Atom{<:Real}, 1}`: セル内のすべての原子のメタデータを格納します。
  * `numbers::Array{<:Integer, 1}`: 元素の原子の数を格納します。
  * `symbols::Array{String, 1}`: 元素の原子の化学記号を格納します。
