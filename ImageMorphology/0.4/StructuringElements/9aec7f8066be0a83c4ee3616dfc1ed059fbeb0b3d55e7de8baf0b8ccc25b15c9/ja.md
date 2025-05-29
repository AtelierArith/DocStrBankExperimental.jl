```
strel_box(A; r=1)
strel_box(size; r=size .÷ 2)
```

すべての要素がローカルウィンドウ内で接続されたN次元構造要素（SE）を構築します。

画像 `A` が提供される場合、SEのサイズはデフォルトの半サイズ `r=1` で `(2r+1, 2r+1, ...)` になります。`size` が提供される場合、デフォルトの `r` は `size .÷ 2` になります。デフォルトの `dims` はすべての次元、すなわち `(1, 2, ..., length(size))` です。

```jldoctest; setup=:(using ImageMorphology; using ImageMorphology.StructuringElements)
julia> img = rand(64, 64);

julia> strel_box(img)
3×3 SEBoxArray{2, UnitRange{Int64}} with indices -1:1×-1:1:
 1  1  1
 1  1  1
 1  1  1

julia> strel_box(img; r=2)
5×5 SEBoxArray{2, UnitRange{Int64}} with indices -2:2×-2:2:
 1  1  1  1  1
 1  1  1  1  1
 1  1  1  1  1
 1  1  1  1  1
 1  1  1  1  1

julia> strel_box((5,5); r=(1,2))
5×5 SEBoxArray{2, UnitRange{Int64}} with indices -2:2×-2:2:
 0  0  0  0  0
 1  1  1  1  1
 1  1  1  1  1
 1  1  1  1  1
 0  0  0  0  0
```

!!! note "特化とパフォーマンス"
    ボックス形状 `SEBox` は、多くの形態学アルゴリズムが効率的な実装を提供する特別なタイプです。このため、`SEBoxArray` を他の配列タイプ（例：`Array{Bool}` を介して `collect`）に収集しようとすると、パフォーマンスが大幅に低下する可能性が非常に高いです。


他にも [`strel`](@ref) と [`strel_box`](@ref) を参照してください。
