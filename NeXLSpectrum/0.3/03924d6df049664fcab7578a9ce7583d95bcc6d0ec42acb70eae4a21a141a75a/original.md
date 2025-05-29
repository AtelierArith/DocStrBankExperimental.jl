```
extract(fd::FilteredReference{T}, roi::UnitRange{Int})::Vector{T} where { T <: AbstractFloat }
extract(fd::FilteredUnknown, roi::UnitRange{Int})::Vector{T} where { T <: AbstractFloat }
```

Extract the filtered data representing the specified range.  `roi` must fully encompass the filtered data in `fd`.
