```
finddelay(x, y)
```

Estimate the delay of x with respect to y by locating the peak of their cross-correlation.

The output delay will be positive when x is delayed with respect y, negative if advanced, 0 otherwise.

# Example

```jldoctest
julia> finddelay([0, 0, 1, 2, 3], [1, 2, 3])
2

julia> finddelay([1, 2, 3], [0, 0, 1, 2, 3])
-2
```
