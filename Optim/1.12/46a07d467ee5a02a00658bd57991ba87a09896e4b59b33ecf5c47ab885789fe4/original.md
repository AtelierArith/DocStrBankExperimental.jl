# GoldenSection

## Constructor

```julia
    GoldenSection(;)
```

## Description

The `GoldenSection` method seeks to minimize a univariate function on an interval `[a, b]`. At all times the algorithm maintains a tuple of three minimizer candidates `(c, d, e)` where $c<d<e$ such that the ratio of the largest to the smallest interval is the Golden Ratio.

## References

https://en.wikipedia.org/wiki/Golden-section_search
