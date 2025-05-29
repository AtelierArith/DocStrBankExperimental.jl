```
..(start, stop)
start..stop
```

Constructs an `Interval(start, stop)`, which represents the closed interval between `start` and `stop`. `Interval`s are abstract collections which support `in` but not iteration, indexing, etc.

The interval includes both the `start` and `stop` poitns. To exclude the `start` or `stop` from the `Interval`, use the `greaterthan` or `lessthan` function.

# Examples

```julia julia> 2 in 1..3 true

julia> 3 in 1..3 true

julia> 4 in 1..3 false

julia> 1 in greaterthan(1)..3 false

julia> 3 in 1..lessthan(3) false
