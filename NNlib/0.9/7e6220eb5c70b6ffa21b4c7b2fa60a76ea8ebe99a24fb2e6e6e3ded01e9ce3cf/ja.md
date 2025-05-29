```
pad_constant(x, pad::Tuple, val = 0; [dims = :])
pad_constant(x, pad::Int, val = 0; [dims = :])
```

配列 `x` を定数値 `val` でパディングします。

`pad` は整数のタプルであることができます。もしそれが `2 * length(dims)` の長さであれば、`dims` の各次元に対する左と右のパディングサイズを `(l1, r1, ..., ln, rn)` として指定します。代わりに `length(dims)` の長さのタプルが供給された場合、対称的なパディングが適用されます。`dims` が指定されていない場合、すべての次元がデフォルトとなります。

整数 `pad` 入力の場合、`dims` のすべての次元の両側に適用されます。

他に [`pad_zeros`](@ref)、[`pad_repeat`](@ref)、[`pad_reflect`](@ref)、[`pad_symmetric`](@ref)、および [`pad_circular`](@ref) も参照してください。

```jldoctest
julia> r = reshape(1:4, 2, 2)
2×2 reshape(::UnitRange{Int64}, 2, 2) with eltype Int64:
 1  3
 2  4

julia> pad_constant(r, (1, 2, 3, 4), 8)
5×9 Matrix{Int64}:
 8  8  8  8  8  8  8  8  8
 8  8  8  1  3  8  8  8  8
 8  8  8  2  4  8  8  8  8
 8  8  8  8  8  8  8  8  8
 8  8  8  8  8  8  8  8  8

julia> pad_constant(r, 1, 8)
4×4 Matrix{Int64}:
 8  8  8  8
 8  1  3  8
 8  2  4  8
 8  8  8  8

julia> r = reshape(1:27, 3, 3, 3)
3×3×3 reshape(::UnitRange{Int64}, 3, 3, 3) with eltype Int64:
[:, :, 1] =
 1  4  7
 2  5  8
 3  6  9

[:, :, 2] =
 10  13  16
 11  14  17
 12  15  18

[:, :, 3] =
 19  22  25
 20  23  26
 21  24  27

julia> pad_constant(r, (2,1), dims = 1) # 非対称パディング
6×3×3 Array{Int64, 3}:
[:, :, 1] =
 0  0  0
 0  0  0
 1  4  7
 2  5  8
 3  6  9
 0  0  0

[:, :, 2] =
  0   0   0
  0   0   0
 10  13  16
 11  14  17
 12  15  18
  0   0   0

[:, :, 3] =
  0   0   0
  0   0   0
 19  22  25
 20  23  26
 21  24  27
  0   0   0

julia> pad_constant(r, (2,1, 3), dims = (1,2)) # パディングは常に dims と同じ長さか、その倍でなければなりません
ERROR: ArgumentError: Could not parse padding (2, 1, 3) and dims (1, 2)
Stacktrace:
[...]
```
