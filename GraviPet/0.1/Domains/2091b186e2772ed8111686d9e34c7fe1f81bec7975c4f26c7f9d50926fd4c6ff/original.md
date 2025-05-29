```
expanded(dom::Domain, delta)::Domain
expanded(dom::Domain, delta_lo, delta_hi)::Domain
```

Expand the domain `dom`. The lower and upper domain bounds are moved by either `delta`, or `delta_lo` and `delta_hi`, respectively. Positive deltas enlarge the domain, negative values shrink it. Domains must be non-empty.

`expanded(dom, delta)` is equivalent to `expanded(dom, delta, delta)`.

See also [`shifted`](@ref).
