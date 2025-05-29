```
pad_reflect(x, pad::Tuple; [dims])
pad_reflect(x, pad::Int; [dims])
```

配列 `x` を境界で値を反映させてパディングします。

`pad` は整数のタプル `(l1, r1, ..., ln, rn)` で、これは `dims` の各次元に対する左と右のパディングサイズを指定します。`dims` が指定されていない場合、最初の `n` 次元がデフォルトとなります。

`pad` が整数の場合、`dims` のすべての次元の両側に適用されます。この場合、`dims` は最初の `ndims(x)-2` 次元（すなわちチャネルとバッチ次元を除外）にデフォルトとなります。

他にも [`pad_repeat`](@ref)、[`pad_symmetric`](@ref)、[`pad_circular`](@ref)、および [`pad_constant`](@ref) を参照してください。

```jldoctest
julia> r = reshape(1:9, 3, 3)
3×3 reshape(::UnitRange{Int64}, 3, 3) with eltype Int64:
 1  4  7
 2  5  8
 3  6  9

julia> pad_reflect(r, (1,2,1,2))
6×6 Matrix{Int64}:
 5  2  5  8  5  2
 4  1  4  7  4  1
 5  2  5  8  5  2
 6  3  6  9  6  3
 5  2  5  8  5  2
 4  1  4  7  4  1
```
