```
insupport(d::UnivariateDistribution, x::Any)
```

When `x` is a scalar, it returns whether x is within the support of `d` (e.g., `insupport(d, x) = minimum(d) <= x <= maximum(d)`). When `x` is an array, it returns whether every element in x is within the support of `d`.

Generic fallback methods are provided, but it is often the case that `insupport` can be done more efficiently, and a specialized `insupport` is thus desirable. You should also override this function if the support is composed of multiple disjoint intervals.
