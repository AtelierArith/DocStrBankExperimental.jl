```
intersect(a::Interval{T}...) where T
```

Returns the n-ary intersection of its arguments.

This function is applicable to any number of input intervals, as in `intersect(a1, a2, a3, a4)` where `ai` is an interval. If your use case needs to splat the input, as in `intersect(a...)`, consider `reduce(intersect, a)` instead, because you save the cost of splatting.
