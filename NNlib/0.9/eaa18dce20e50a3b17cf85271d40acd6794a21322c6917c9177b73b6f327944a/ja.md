```
pad_circular(x, pad::Tuple; [dims])
pad_circular(x, pad::Int; [dims])
```

配列 `x` を境界で「円形」にパディングし、`x` の反対側から値をラップアラウンドします。

`pad` は整数のタプル `(l1, r1, ..., ln, rn)` で、`dims` の各次元に対する左と右のパディングサイズを指定する長さ `2n` のものです。`dims` が指定されていない場合、最初の `n` 次元がデフォルトとなります。

`pad` が整数の場合、`dims` のすべての次元の両側に適用されます。この場合、`dims` は最初の `ndims(x)-2` 次元（すなわちチャネルとバッチ次元を除外）にデフォルト設定されます。

任意の次元のいずれかの側のパッド長は、その次元における `x` のサイズを超えてはならず、すなわち `pad_circular` は `x` の任意のサイズのタイルを作成することはできません。

他にも [`pad_repeat`](@ref)、[`pad_reflect`](@ref)、[`pad_symmetric`](@ref)、および [`pad_constant`](@ref) を参照してください。

```jldoctest
julia> r = reshape(1:9, 3, 3)
3×3 reshape(::UnitRange{Int64}, 3, 3) with eltype Int64:
 1  4  7
 2  5  8
 3  6  9

julia> pad_circular(r, (1,2,1,2))
6×6 Matrix{Int64}:
 9  3  6  9  3  6
 7  1  4  7  1  4
 8  2  5  8  2  5
 9  3  6  9  3  6
 7  1  4  7  1  4
 8  2  5  8  2  5
```
