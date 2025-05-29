```
findsample(dt::AbstractDataTable{A, S}, sample::T) where {A, S, T <: S}
findsample(dt::AbstractDataTable, sample::Symbol)
```

Return the index of the first element of `sampleobj(dt)` or `samplename(dt)` for which the element equals to `sample`.
