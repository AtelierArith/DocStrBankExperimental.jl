```
range(i::Interval{:closed,:open}; length)
range(i::Interval{:closed,:open}, length::Integer)
range(i::Interval{:open,:closed}; length)
range(i::Interval{:open,:closed}, length::Integer)
```

Constructs a range of a specified length with `step=width(i)/length`.

# Examples

```jldoctest
julia> range(iv"[1, 2)", 7)  # Does not contain right endpoint
1.0:0.14285714285714285:1.8571428571428572

julia> range(iv"(1, 2]", 7)  # Does not contain left endpoint
1.1428571428571428:0.14285714285714285:2.0

julia> range(1, 2, 8)
1.0:0.14285714285714285:2.0
```
