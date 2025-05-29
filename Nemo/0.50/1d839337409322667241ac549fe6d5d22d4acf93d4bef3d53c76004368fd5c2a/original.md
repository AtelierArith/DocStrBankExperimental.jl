```
Float64(x::RealFieldElem, round::RoundingMode=RoundNearest)
```

Converts $x$ to a `Float64`, rounded in the direction specified by $round$. For `RoundNearest` the return value approximates the midpoint of $x$. For `RoundDown` or `RoundUp` the return value is a lower bound or upper bound for all values in $x$.
