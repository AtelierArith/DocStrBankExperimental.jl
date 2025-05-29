```
frechet_mono_via_refinement( P, Q, approx )

Computes the "true" monotone Frechet distance between P and Q,
using the ve_r algorithm. It does refinement, to add vertices if
needed to get monotonicity. Note, that there is an eps parameter -
for real inputs you can set it quite small. In any case, in the
worst case it only approximates the Frechet (monotone)
distance. It returns a morphing, and a boolean that is true if the
result is the true Frechet distance.

Observe, that this function might be too slow if the two curves
are huge, since it does not simplify them before computing the
distance.
```

# Returns

Returns a 4-tuple  ( m, f, P, Q ): `m`: Morphing realizing result. `f`: Is distance returned is the exact continuous Frechet distance. `P`: Refined first input polygon `Q`: Refined second input polygon

'out' if specified returns the middle morphings used in computing the       solution.
