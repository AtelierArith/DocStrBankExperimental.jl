```
aligntime(col::AbstractArray, time::ScaledArrOrSub)
aligntime(col::AbstractArray, time::RotatingTimeArray)
aligntime(data, colname::Union{Symbol,Integer}, timename::Union{Symbol,Integer})
```

時間値の列 `col` を [`ScaledArray`](@ref) に変換します。このとき、`pool` は `time` の [`ScaledArray`](@ref) と同じ最初の要素とステップサイズを持ちます。もし `time` が [`RotatingTimeArray`](@ref) であり、`time` フィールドが [`ScaledArray`](@ref) である場合、返される配列も [`RotatingTimeArray`](@ref) であり、`time` フィールドは変換された [`ScaledArray`](@ref) になります。代わりに、配列は `Tables.jl` 互換の `data` テーブルと列インデックス `colname` および `timename` で指定することもできます。詳細は [`settime`](@ref) を参照してください。

これは、すべての離散化された時間期間を同じスケールで表現するのに役立ち、`DataAPI.refarray` によって返される基礎となる参照値が列間で直接比較可能になります。 ```
