```
time_from_index(sample_rate, sample_index)
```

Given `sample_rate` in Hz and assuming `sample_index > 0`, return the earliest `Nanosecond` containing `sample_index`.

Examples:

```jldoctest
julia> time_from_index(1, 1)
0 nanoseconds

julia> time_from_index(1, 2)
1000000000 nanoseconds

julia> time_from_index(100, 100)
990000000 nanoseconds

julia> time_from_index(100, 101)
1000000000 nanoseconds
```
