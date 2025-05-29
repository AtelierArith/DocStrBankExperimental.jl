```
chunk(x, partition_idxs; [npartitions, dims])
```

配列 `x` を、`partition_idxs` のインデックスに従って、次元 `dims` に沿って分割します。

`partition_idxs` はソートされている必要があり、1 からパーティションの数の間の正の整数のみを含む必要があります。

パーティションの数 `npartitions` が提供されていない場合、`partition_idxs` から推測されます。

`dims` が提供されていない場合、デフォルトで最後の次元になります。

詳細は [`unbatch`](@ref) を参照してください。

# 例

```jldoctest
julia> x = reshape([1:10;], 2, 5)
2×5 Matrix{Int64}:
 1  3  5  7   9
 2  4  6  8  10

julia> chunk(x, [1, 2, 2, 3, 3])
3-element Vector{SubArray{Int64, 2, Matrix{Int64}, Tuple{Base.Slice{Base.OneTo{Int64}}, UnitRange{Int64}}, true}}:
 [1; 2;;]
 [3 5; 4 6]
 [7 9; 8 10]
```
