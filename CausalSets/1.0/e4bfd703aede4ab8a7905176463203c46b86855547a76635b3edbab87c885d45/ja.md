```
cardinality_abundances(causet[, max_cardinality]) -> Vector{Int64}
```

`causet`内のすべての基数の豊富さをカウントします。

結果のベクトルのインデックスは1つずれており、インデックス `i+1` には、基数 $i$ の鎖の数が含まれます。したがって、結果のベクトルの長さは `length(causet) + 1` になります。

`max_cardinality` が指定されている場合、この関数は `max_cardinality` までの基数のみをカウントします。その場合、結果のベクトルの長さは `max_cardinalities` になります。
