```
chain_cardinality_abundances(causet, ::Val{N}[, max_cardinality]) -> Array{Int64, N}
```

`causet`内のすべてのチェーンのカーディナリティの豊富さをカウントします。

返される配列のインデックスは1つシフトされています。たとえば、`N = 3`の場合、インデックス`(i+1, j+1, k+1)`には、`causet`内のチェーンカーディナリティ$(i, j, k)$を持つチェーンのカウントが含まれます。したがって、結果の配列はそれぞれ`length(causet) + 1`のサイズを持つ`N`軸を持ちます。

パラメータ`max_cardinality`が指定されている場合、この関数は、個々のカーディナリティが`max_cardinality`以下のチェーンカーディナリティのみをカウントします。したがって、この場合、結果の配列の軸はそれぞれ`max_cardinality`のサイズのみを持ちます。
