```
swap_rows(a::MatrixElem{T}, i::Int, j::Int) where T <: NCRingElement
```

行列 $a$ の $i$ 行目と $j$ 行目を入れ替えた行列 $b$ を返します。

# 例

```jldoctest
julia> M = identity_matrix(ZZ, 3)
[1   0   0]
[0   1   0]
[0   0   1]

julia> swap_rows(M, 1, 2)
[0   1   0]
[1   0   0]
[0   0   1]

julia> M  # 修正されていない
[1   0   0]
[0   1   0]
[0   0   1]
```
