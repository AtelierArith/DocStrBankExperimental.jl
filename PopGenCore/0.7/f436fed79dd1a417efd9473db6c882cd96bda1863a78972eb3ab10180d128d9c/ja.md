```
mutable struct PopDataInfo
    samples::Int64
    sampeinfo::DataFrame
    loci::Int64
    locusinfo::DataFrame
    populations::Int64
    ploidy::Union{Int8, Vector{Int8}}
    biallelic::Bool
end
```

`PopData.metadata` フィールドとして内部で使用されるデータ構造で、`PopData` に関する基本情報を簡単にアクセスできるように保存します。
