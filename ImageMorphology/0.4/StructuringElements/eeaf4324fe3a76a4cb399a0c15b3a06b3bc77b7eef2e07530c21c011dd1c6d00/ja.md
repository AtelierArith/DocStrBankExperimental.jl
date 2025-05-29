```
strel_size(x)
```

構造要素を含む最小ブロックサイズを計算します。結果は奇数の整数のタプルになります。

```jldoctest; setup=:(using ImageMorphology; using ImageMorphology.StructuringElements)
julia> se = strel_diamond((5, 5); r=1)
5×5 SEDiamondArray{2, 2, UnitRange{Int64}, 0} with indices -2:2×-2:2:
 0  0  0  0  0
 0  0  1  0  0
 0  1  1  1  0
 0  0  1  0  0
 0  0  0  0  0

julia> strel_size(se) # は (5, 5) ではありません
(3, 3)

julia> strel(Bool, strel(CartesianIndex, se)) # 最小の囲むブロックのみをチェックするため
3×3 OffsetArray(::BitMatrix, -1:1, -1:1) with eltype Bool with indices -1:1×-1:1:
 0  1  0
 1  1  1
 0  1  0

julia> se = [CartesianIndex(1, 1), CartesianIndex(-2, -2)];

julia> strel_size(se) # は (4, 4) ではありません
(5, 5)

julia> strel(Bool, se) # 接続マスクは奇数サイズでなければならないため
5×5 OffsetArray(::BitMatrix, -2:2, -2:2) with eltype Bool with indices -2:2×-2:2:
 1  0  0  0  0
 0  0  0  0  0
 0  0  1  0  0
 0  0  0  1  0
 0  0  0  0  0

julia> se = strel_diamond((5, 5), (1, ); r=1)
5×5 SEDiamondArray{2, 1, UnitRange{Int64}, 1} with indices -2:2×-2:2:
 0  0  0  0  0
 0  0  1  0  0
 0  0  1  0  0
 0  0  1  0  0
 0  0  0  0  0

julia> strel_size(se)
(3, 1)
```
