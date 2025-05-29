```
terminate!(pa::Path{T}; gap=Paths.terminationlength(pa), rounding=zero(T), initial=false) where {T}
```

End a `Paths.Path` with a termination.

If the preceding style is a CPW, this is a "short termination" if `iszero(gap)` and is an "open termination" with a gap of `gap` otherwise, defaulting to the gap of the preceding CPW.

Rounding of corners may be specified with radius given by `rounding`. Rounding keeps the trace length constant by removing some length from the preceding segment and adding a rounded section of equivalent maximum length.

Terminations can be applied on curves without changing the underlying curve. If you add a segment after a termination, it will start a straight distance `gap` away from where the original curve ended. However, rounded terminations are always drawn as though straight from the point where rounding starts, slightly before the end of the curve. This allows the rounded corners to be represented as exact circular arcs.

If the preceding style is a trace, the termination only rounds the corners at the end of the segment or does nothing if `iszero(rounding)`.

If `initial`, the termination is appended before the beginning of the `Path`.
