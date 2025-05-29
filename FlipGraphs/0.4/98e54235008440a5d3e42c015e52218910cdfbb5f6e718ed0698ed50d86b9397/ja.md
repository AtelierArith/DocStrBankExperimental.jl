```
relative_degree(A::Matrix{<:Integer}, u::Integer, V::Vector{<:Integer}) :: Int32
```

点 `V` の部分集合内の任意の頂点に向かう `u` からのエッジの数を計算します。

# 引数

-`A::Matrix{<:Integer}`: 隣接行列。`A[i,j] = 1` であれば、`i` から `j` へのエッジが存在します。
