```
strel([T], X::AbstractArray)
```

構造要素（SE）`X`を、要素型`T`に適した表現形式に変換します。これは、ほとんどのImageMorphology関数が理解するSEを生成するための便利なツールです。

ImageMorphologyは現在、一般的に使用される2つの表現をサポートしています：

  * `T=CartesianIndex`：中心点へのオフセット。出力型は`Vector{CartesianIndex{N}}`です。
  * `T=Bool`：接続マスクで、`true`は中心点に接続されていることを示します。出力型は`BitArray{N}`です。

```jldoctest; setup=:(using ImageMorphology)
julia> se_mask = centered(Bool[1 1 0; 1 1 0; 0 0 0]) # 接続マスク
3×3 OffsetArray(::Matrix{Bool}, -1:1, -1:1) with eltype Bool with indices -1:1×-1:1:
 1  1  0
 1  1  0
 0  0  0

julia> se_offsets = strel(CartesianIndex, se_mask) # 中心点への変位オフセット
3-element Vector{CartesianIndex{2}}:
 CartesianIndex(-1, -1)
 CartesianIndex(0, -1)
 CartesianIndex(-1, 0)

julia> se = strel(Bool, se_offsets)
3×3 OffsetArray(::BitMatrix, -1:1, -1:1) with eltype Bool with indices -1:1×-1:1:
 1  1  0
 1  1  0
 0  0  0
```

他にも、2つの特別なケースのSEコンストラクタについては[`strel_diamond`](@ref)および[`strel_box`](@ref)を参照してください。
