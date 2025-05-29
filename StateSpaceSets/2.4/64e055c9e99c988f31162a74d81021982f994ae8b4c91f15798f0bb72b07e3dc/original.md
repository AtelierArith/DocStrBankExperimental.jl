```
statespace_sampler(grid::NTuple{N, AbstractRange} [, seed])
```

If given a `grid` that is a tuple of `AbstractVector`s, the minimum and maximum of the vectors are used to make an `HRectangle` region.
