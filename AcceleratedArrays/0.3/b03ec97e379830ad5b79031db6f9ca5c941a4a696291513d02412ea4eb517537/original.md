```
Interval(start, stop)
```

Construct a closed interval, which is a collection which contains (via `in`) elements between `start` and `stop` (inclusive) according to `isless`. The collection is abstract in nature and doesn't support iteration, indexing, etc.

Can be constructed via the `..` function, e.g. `1..3 === Interval(1, 3)`.

# Examples

```julia julia> 2 in Interval(1, 3) true

julia> 3 in Interval(1, 3) true

julia> 4 in Interval(1, 3) false
