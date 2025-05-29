An `CumSum(a::Accumulator)` gets updated each time that  `a` does. The time for an update and retrieval is both `O(log(length(a)))`. It is normally constructed with `cumsum(a)`, which takes  time `O(1)`

```
julia> a = Accumulator([1:10;])
10-element Accumulator{Int64, +, zero}:
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10

julia> c = cumsum(a)
CumSum(Accumulator([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]))

julia> c[end]
55

julia> a[1] = 100
100

julia> c[end]
154
```
