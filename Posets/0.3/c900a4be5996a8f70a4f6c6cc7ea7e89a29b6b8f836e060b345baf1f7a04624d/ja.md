```
chain(vlist::Vector{T}) where {T<:Integer}
```

`vlist` から要素を引き出してチェーンを作成します。`vlist` は `1:n` の順列でなければなりません。例えば、`chain([2,1,3])` は `2 < 1 < 3` の順序集合を返します。
