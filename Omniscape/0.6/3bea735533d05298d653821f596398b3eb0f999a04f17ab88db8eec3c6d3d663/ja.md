```
missingarray(A::Array{T, N}, T::DataType, nodata::Number)
```

この関数は配列を `MissingArray` に変換し、出力内の `nodata` 値を `missing` に置き換えます。 `MissingArray{T, N}` は `Array{Union{T, Missing}, N}` のエイリアスです。この関数は [`run_omniscape`](@ref) の入力を準備するために使用できます。

# パラメータ

**`A`**: 変換する配列。

**`T`**: 出力のデータ型（例: Float64 または Float32）。

**`nodata`**: 結果内で `missing` に置き換えられる数値。
