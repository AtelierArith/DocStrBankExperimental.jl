```
index_from_time(sample_rate, span)
```

Return the `UnitRange` of indices corresponding to `span` given `sample_rate` in Hz:

```jldoctest
julia> index_from_time(100, TimeSpan(Second(0), Second(1)))
1:100

julia> index_from_time(100, TimeSpan(Second(1)))
101:101

julia> index_from_time(100, TimeSpan(Second(3), Second(6)))
301:600
```
