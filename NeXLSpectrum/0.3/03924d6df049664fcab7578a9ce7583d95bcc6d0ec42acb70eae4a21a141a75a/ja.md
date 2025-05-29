```
extract(fd::FilteredReference{T}, roi::UnitRange{Int})::Vector{T} where { T <: AbstractFloat }
extract(fd::FilteredUnknown, roi::UnitRange{Int})::Vector{T} where { T <: AbstractFloat }
```

指定された範囲を表すフィルタリングされたデータを抽出します。`roi`は`fd`内のフィルタリングされたデータを完全に包含する必要があります。
