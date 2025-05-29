```
extreme_filter(f, A; r=1, [dims]) -> out
extreme_filter(f, A, Ω) -> out
```

配列 `A` を、各 Ω-近傍に対して選択関数 `f(x, y)` を使用してフィルタリングします。「extreme」という名前は、典型的な選択関数 `f` の選択が `min` と `max` であることに由来します。

配列 `A` の各ピクセル `p` に対して、選択関数 `f` がその Ω-近傍に対して反復的に適用されます。これは `f(...(f(f(A[p], A[p+Ω[1]]), A[p+Ω[2]]), ...)` のような形です。たとえば、1次元の場合、各 `p` に対して `out[p] = f(f(A[p], A[p-1]), A[p+1])` がデフォルトの動作です。

Ω-近傍は `dims` または `Ω` 引数によって定義されます。`r` と `dims` キーワードは、[`strel_box`](@ref) を使用してボックス形状の近傍 `Ω` を指定します。`Ω` は構造要素 (SE) とも呼ばれ、移動オフセットまたはブール配列マスクのいずれかであることができます。詳細については、[`strel`](@ref) を参照してください。

# 例

```jldoctest extreme_filter; setup=:(using ImageMorphology)
julia> M = [4 6 5 3 4; 8 6 9 4 8; 7 8 4 9 6; 6 2 2 1 7; 1 6 5 2 6]
5×5 Matrix{Int64}:
 4  6  5  3  4
 8  6  9  4  8
 7  8  4  9  6
 6  2  2  1  7
 1  6  5  2  6

julia> extreme_filter(max, M) # 4つの直接隣接点を使用した最大フィルタ
5×5 Matrix{Int64}:
 8  9  9  9  8
 8  9  9  9  9
 8  9  9  9  9
 8  8  9  9  9
 6  6  6  7  7

julia> extreme_filter(max, M; dims=1) # 最初の次元（列）に沿った最大フィルタ
5×5 Matrix{Int64}:
 8  6  9  4  8
 8  8  9  9  8
 8  8  9  9  8
 7  8  5  9  7
 6  6  5  2  7
```

`Ω` は、接続性を示す `true` 要素を持つ `AbstractArray{Bool}` マスク配列、または中心要素への移動オフセットを示す各要素を持つ `AbstractArray{<:CartesianIndex}` 配列のいずれかです。

```jldoctest extreme_filter
julia> Ω_mask = centered(Bool[1 1 0; 1 1 0; 1 0 0]) # マスク形式のカスタム近傍
3×3 OffsetArray(::Matrix{Bool}, -1:1, -1:1) with eltype Bool with indices -1:1×-1:1:
 1  1  0
 1  1  0
 1  0  0

julia> out = extreme_filter(max, M, Ω_mask)
5×5 Matrix{Int64}:
 4  8  6  9  4
 8  8  9  9  9
 8  8  9  9  9
 7  8  8  9  9
 6  6  6  5  7

julia> Ω_offsets = strel(CartesianIndex, Ω_mask) # 移動オフセットとしてのカスタム近傍
4-element Vector{CartesianIndex{2}}:
 CartesianIndex(-1, -1)
 CartesianIndex(0, -1)
 CartesianIndex(1, -1)
 CartesianIndex(-1, 0)

julia> out == extreme_filter(max, M, Ω_offsets) # 両方のバージョンは同等に機能する
true
```

インプレースバージョン [`extreme_filter!`](@ref) も参照してください。ImageFiltering パッケージの別の関数 `ImageFiltering.mapwindow` は、同様の機能を提供します。 ```
