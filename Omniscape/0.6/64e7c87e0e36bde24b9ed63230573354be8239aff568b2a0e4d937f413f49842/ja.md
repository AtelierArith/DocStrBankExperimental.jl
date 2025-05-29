```
missing_array_to_array(A::MissingArray{T, N}, nodata::Number)
```

この関数は、`MissingArray` 型の配列を数値配列に変換し、`missing` エントリを `nodata` で置き換えます。`MissingArray{T, N}` は `Array{Union{T, Missing}, N}` のエイリアスです。

# パラメータ

**`A`**: 変換する配列。

**`nodata`**: 結果の `missing` 値を置き換える数値。
