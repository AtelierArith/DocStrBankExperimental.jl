```
find_knot_interval(ts::AbstractVector, x::Real, [ileft = nothing]) -> (i, zone)
```

Finds the index $i$ corresponding to the knot interval $[t_i, t_{i + 1}]$ that should be used to evaluate B-splines at location $x$.

The knot vector is assumed to be sorted in non-decreasing order.

It also returns a `zone` integer, which is:

  * `0`  if `x` is within the knot domain (`ts[begin] ≤ x ≤ ts[end]`),
  * `-1` if `x < ts[begin]`,
  * `1`  if `x > ts[end]`.

This function is functionally equivalent to de Boor's `INTERV` routine (de Boor 2001, p. 74).

If one already knows the location `i` associated to the knot interval, then one can pass it as the optional `ileft` argument, in which case only the zone needs to be computed.
