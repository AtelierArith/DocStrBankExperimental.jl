```julia
GetAllOffsets(OffsetRange::Int64, dim::Int64) --> Vector{Vector{Int64}}
```

範囲を指定すると、オフセットベクトルの各要素が[-`OffsetRange`, `OffsetRange`]の範囲内にあるようなすべての可能なボンドオフセットの集合を返します。
