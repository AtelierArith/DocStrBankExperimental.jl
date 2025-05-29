```
block_diagonal_matrix(V::Vector{<:MatElem{T}}) where T <: NCRingElement
```

ベクトル `V` に与えられた行列からブロック対角行列を作成します。`V` には少なくとも1つの行列が含まれている必要があります。
