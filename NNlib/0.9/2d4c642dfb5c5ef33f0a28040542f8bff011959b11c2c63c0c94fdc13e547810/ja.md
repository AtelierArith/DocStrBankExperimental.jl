```
pad_repeat(x, pad::Tuple; [dims])
pad_repeat(x, pad::Int; [dims])
```

配列 `x` を境界の値を繰り返してパディングします。

`pad` は整数のタプル `(l1, r1, ..., ln, rn)` で、これは `dims` の各次元に対する左と右のパディングサイズを指定します。`dims` が指定されていない場合、デフォルトで最初の `n` 次元になります。

`pad` が整数の場合、`dims` のすべての次元の両側に適用されます。この場合、`dims` は最初の `ndims(x)-2` 次元（すなわち、チャネルとバッチ次元を除外）にデフォルト設定されます。

他にも [`pad_reflect`](@ref)、[`pad_symmetric`](@ref)、[`pad_circular`](@ref)、および [`pad_constant`](@ref) を参照してください。

```jldoctest
julia> r = reshape(1:9, 3, 3)
3×3 reshape(::UnitRange{Int64}, 3, 3) with eltype Int64:
 1  4  7
 2  5  8
 3  6  9

julia> pad_repeat(r, (1,2,3,4))
6×10 Matrix{Int64}:
 1  1  1  1  4  7  7  7  7  7
 1  1  1  1  4  7  7  7  7  7
 2  2  2  2  5  8  8  8  8  8
 3  3  3  3  6  9  9  9  9  9
 3  3  3  3  6  9  9  9  9  9
 3  3  3  3  6  9  9  9  9  9
```
