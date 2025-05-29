```
extrapolate(fh_itr; power=1,
                    atol=0, rtol=0, maxeval=typemax(Int), breaktol=Inf)
```

Similar to `extrapolate(f, h)`, performs Richardson extrapolation of a sequence of values `f(h)` to `h → 0`, but takes an iterable collection `fh_itr` of a sequence of `(f(h), h)` tuples (in order of decreasing `|h|`).

There is no `contract` keyword argument since the contraction factors are determined by the sequence of `h` values (which need not contract by the same amount).  The tolerances `atol` and `rtol` both default to `0` so that by default it examines *all* of the values in the `fh_itr` collection.   Otherwise, the keyword arguments have the same meanings as in `extrapolate(f, h)`.
