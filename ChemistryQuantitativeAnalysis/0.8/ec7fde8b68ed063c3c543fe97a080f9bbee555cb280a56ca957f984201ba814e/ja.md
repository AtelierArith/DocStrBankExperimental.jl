```
findsample(dt::AbstractDataTable{A, S}, sample::T) where {A, S, T <: S}
findsample(dt::AbstractDataTable, sample::Symbol)
```

`sampleobj(dt)` または `samplename(dt)` の最初の要素のインデックスを返します。その要素が `sample` と等しい場合です。
