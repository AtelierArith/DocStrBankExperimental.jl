```
aut(F::T)::NamedTuple{(:gen, :size),Tuple{Vector{Vector{Int64}},Int64}} where {T<:Flag}
```

`F` の自己同型群。フィールドを持つ名前付きタプルを返します。

  * `gen::Vector{Vector{Int}}`: すべての自己同型を生成する置換のベクトル。
  * `size::Int`: `F` の自己同型群のサイズ。
