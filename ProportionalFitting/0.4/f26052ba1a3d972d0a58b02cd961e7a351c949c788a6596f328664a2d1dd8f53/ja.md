```
DimIndices(idx::Vector{Vector{Int}})
```

DimIndicesは配列の次元のためのインデックスの完全なリストを表します。これは、整数のネストされたベクターである単一の要素`idx`を含むオブジェクトです。例えば、`[[2], [1, 3], [4]]`のようになります。DimIndicesオブジェクトは、一意性と完全性がチェックされます。つまり、最大のインデックスまでのすべてのインデックスが正確に1回使用されます。

# フィールド

  * `idx::Vector{Vector{Int}}`: 次元インデックスのネストされたベクター。

# 例

```julia-repl
julia> DimIndices([2, [1, 3], 4])
Indices for 4D array:
[[2], [1, 3], [4]]
```
