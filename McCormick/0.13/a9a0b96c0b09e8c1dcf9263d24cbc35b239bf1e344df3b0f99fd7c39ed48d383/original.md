```julia
intersect(
    x::McCormick.MC{N, T<:Union{McCormick.MV, McCormick.NS}},
    y::McCormick.MC{N, T<:Union{McCormick.MV, McCormick.NS}}
) -> McCormick.MC{N, T} where {N, T<:Union{McCormick.MV, McCormick.NS}}

```

Intersects two McCormick objects by computing setting `cv = max(cv1, cv2)` and `cc = min(cc1, cc2)` with appropriate subgradients. Interval are intersected in the usual fashion. Note that in a typical reverse propagation scheme this may result in `cv > cc` due to rounding error. This is addressed in the following manner:

  * if `cv - cc < MC_INTERSECT_TOL` and `diam(x.Intv ∩ y.Intv) > 3*MC_INTERSECT_TOL`,

then `cv = max(cv - MC_INTERSECT_TOL, Intv.lo)` and `cc = min(cc - MC_INTERSECT_TOL, Intv.hi)`. Subgradients set to zero if `cv == Intv.lo` or `cc == Intv.hi`.

  * if `cv - cc < MC_INTERSECT_TOL` and `diam(x.Intv ∩ y.Intv) < 3*MC_INTERSECT_TOL` and

`MC_INTERSECT_NOOP_FALLBACK == true` then return `x`.

  * else return `MC{N,T}(NaN, NaN, x.Intv ∩ y.Intv, ...)`
