```
strel_diamond(A::AbstractArray, [dims]; r=1)
strel_diamond(size, [dims]; [r])
```

ダイヤモンド形状のN次元構造要素（SE）を構築します。

画像 `A` が提供される場合、SEのサイズはデフォルトの半サイズ `r=1` で `(2r+1, 2r+1, ...)` になります。`size` が提供される場合、デフォルトの `r` は `maximum(size)÷2` になります。デフォルトの `dims` はすべての次元、すなわち `(1, 2, ..., length(size))` です。

```jldoctest; setup=:(using ImageMorphology; using ImageMorphology.StructuringElements)
julia> img = rand(64, 64);

julia> strel_diamond(img) # 画像入力のデフォルトサイズは (3, 3)
3×3 SEDiamondArray{2, 2, UnitRange{Int64}, 0} with indices -1:1×-1:1:
 0  1  0
 1  1  1
 0  1  0

julia> strel_diamond(img; r=2) # `strel_diamond((5,5))` と同等
5×5 SEDiamondArray{2, 2, UnitRange{Int64}, 0} with indices -2:2×-2:2:
 0  0  1  0  0
 0  1  1  1  0
 1  1  1  1  1
 0  1  1  1  0
 0  0  1  0  0

julia> strel_diamond(img, (1,)) # 次元1に沿ったマスク
3×1 SEDiamondArray{2, 1, UnitRange{Int64}, 1} with indices -1:1×0:0:
 1
 1
 1

julia> strel_diamond((3,3), (1,)) # 次元1に沿った3×3マスク
3×3 SEDiamondArray{2, 1, UnitRange{Int64}, 1} with indices -1:1×-1:1:
 0  1  0
 0  1  0
 0  1  0
```

!!! note "特化とパフォーマンス"
    ダイヤモンド形状の `SEDiamond` は、より多くの形態学アルゴリズムがはるかに効率的な実装を提供する特別なタイプです。このため、`SEDiamondArray` を他の配列タイプ（例：`collect` を介して `Array{Bool}`）に収集しようとすると、パフォーマンスが大幅に低下する可能性が非常に高いです。


[`strel`](@ref) および [`strel_box`](@ref) も参照してください。
