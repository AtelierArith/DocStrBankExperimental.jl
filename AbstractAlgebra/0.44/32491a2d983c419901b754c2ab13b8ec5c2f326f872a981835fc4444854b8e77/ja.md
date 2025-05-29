```
swap_rows!(a::MatrixElem{T}, i::Int, j::Int) where T <: NCRingElement
```

$$
a
$$

の$i$行目と$j$行目をその場で入れ替えます。この関数は変更された行列を返します（行列はAbstractAlgebra.jlで可変であると仮定されています）。

# 例

```jldoctest
julia> M = identity_matrix(ZZ, 3)
[1   0   0]
[0   1   0]
[0   0   1]

julia> swap_rows!(M, 1, 2)
[0   1   0]
[1   0   0]
[0   0   1]

julia> M  # 変更されました
[0   1   0]
[1   0   0]
[0   0   1]
```
