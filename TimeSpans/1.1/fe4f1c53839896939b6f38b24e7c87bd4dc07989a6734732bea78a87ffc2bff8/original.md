```
index_from_time(sample_rate, sample_time::Period)
```

Given `sample_rate` in Hz, return the integer index of the most recent sample taken at `sample_time`. Note that `sample_time` must be non-negative and support `convert(Nanosecond, sample_time)`.

Examples:

```jldoctest
julia> index_from_time(1, Second(0))
1

julia> index_from_time(1, Second(1))
2

julia> index_from_time(100, Millisecond(999))
100

julia> index_from_time(100, Millisecond(1000))
101
```
