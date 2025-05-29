```
pad_symmetric(x, pad::Tuple; [dims])
pad_symmetric(x, pad::Int; [dims])
```

配列 `x` を境界に対して対称的に値を反映させてパディングします。つまり、`x` の境界値がパディング値に含まれます。これは [`pad_reflect`](@ref) とは対照的です。

`pad` は整数のタプル `(l1, r1, ..., ln, rn)` で、長さ `2n` のもので、`dims` の各次元に対する左側と右側のパディングサイズを指定します。`dims` が指定されていない場合、最初の `n` 次元がデフォルトとなります。

`pad` が整数の場合、`dims` のすべての次元の両側に適用されます。この場合、`dims` は最初の `ndims(x)-2` 次元（すなわち、チャネルとバッチ次元を除外）にデフォルト設定されます。

他にも [`pad_repeat`](@ref)、[`pad_reflect`](@ref)、[`pad_circular`](@ref)、および [`pad_constant`](@ref) を参照してください。

```jldoctest
julia> r = reshape(1:9, 3, 3)
3×3 reshape(::UnitRange{Int64}, 3, 3) with eltype Int64:
 1  4  7
 2  5  8
 3  6  9

julia> pad_symmetric(r, (1,2,1,2))
6×6 Matrix{Int64}:
 1  1  4  7  7  4
 1  1  4  7  7  4
 2  2  5  8  8  5
 3  3  6  9  9  6
 3  3  6  9  9  6
 2  2  5  8  8  5
```
