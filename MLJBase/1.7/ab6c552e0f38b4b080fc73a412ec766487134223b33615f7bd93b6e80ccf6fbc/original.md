```
iterator([rng, ], r::NominalRange, [,n])
iterator([rng, ], r::NumericRange, n)
```

Return an iterator (currently a vector) for a `ParamRange` object `r`. In the first case iteration is over all `values` stored in the range (or just the first `n`, if `n` is specified). In the second case, the iteration is over approximately `n` ordered values, generated as follows:

1. First, exactly `n` values are generated between `U` and `L`, with a spacing determined by `r.scale` (uniform if `scale=:linear`) where `U` and `L` are given by the following table:

    | `r.lower` | `r.upper` |                 `L` |                 `U` |
    | ---------:| ---------:| -------------------:| -------------------:|
    |    finite |    finite |           `r.lower` |           `r.upper` |
    |    `-Inf` |    finite | `r.upper - 2r.unit` |           `r.upper` |
    |    finite |     `Inf` |           `r.lower` | `r.lower + 2r.unit` |
    |    `-Inf` |     `Inf` | `r.origin - r.unit` | `r.origin + r.unit` |
2. If a callable `f` is provided as `scale`, then a uniform spacing is always applied in (1) but `f` is broadcast over the results. (Unlike ordinary scales, this alters the effective range of values generated, instead of just altering the spacing.)
3. If `r` is a discrete numeric range (`r isa NumericRange{<:Integer}`) then the values are additionally rounded, with any duplicate values removed. Otherwise all the values are used (and there are exacltly `n` of them).
4. Finally, if a random number generator `rng` is specified, then the values are returned in random order (sampling without replacement), and otherwise they are returned in numeric order, or in the order provided to the range constructor, in the case of a `NominalRange`.
