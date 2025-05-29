```julia
intersect(
    x::McCormick.MC{N, McCormick.Diff},
    y::McCormick.MC{N, McCormick.Diff}
) -> McCormick.MC{N, McCormick.Diff} where N

```

Intersects two `MC{N, Diff}` in a manner than preserves differentiability. Interval are intersected in the usual fashion. Note that in a typical reverse propagation scheme this may result in `cv > cc` due to rounding error. This is addressed in the following manner:

  * if `cv - cc < MC_INTERSECT_TOL` and `diam(x.Intv ∩ y.Intv) > 3*MC_INTERSECT_TOL`,

then `cv = max(cv - MC_INTERSECT_TOL, Intv.lo)` and `cc = min(cc - MC_INTERSECT_TOL, Intv.hi)`. Subgradients set to zero if `cv == Intv.lo` or `cc == Intv.hi`.

  * if `cv - cc < MC_INTERSECT_TOL` and `diam(x.Intv ∩ y.Intv) < 3*MC_INTERSECT_TOL` and

`MC_INTERSECT_NOOP_FALLBACK == true` then return `x`.

  * else return `MC{N,T}(NaN, NaN, x.Intv ∩ y.Intv, ...)`
