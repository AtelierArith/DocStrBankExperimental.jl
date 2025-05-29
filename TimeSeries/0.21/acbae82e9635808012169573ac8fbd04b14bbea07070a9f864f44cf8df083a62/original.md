```
merge(ta1::TimeArray{T}, ta2::TimeArray{T}, [tas::TimeArray{T}...];
      method = :inner, colnames = [...], padvalue = NaN)
```

Merge several `TimeArray`s along with the time index.

## Argument

  * `method::Symbol`: `:inner`, `:outer`, `:left` or `:right`.
