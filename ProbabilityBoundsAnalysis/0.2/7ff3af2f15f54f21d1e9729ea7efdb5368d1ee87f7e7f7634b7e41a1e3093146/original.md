```
pbox( x :: Array{Interval{T}, 1} ) where T <: Real
```

Constructs a pbox from an array of intervals with equal mass. Left and right bounds are sorted to construct cdf bounds.
