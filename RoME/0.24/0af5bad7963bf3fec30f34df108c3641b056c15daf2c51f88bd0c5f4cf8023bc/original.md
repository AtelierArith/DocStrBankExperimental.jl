```julia
generateGraph_Helix2DSpiral!(; ...)
generateGraph_Helix2DSpiral!(
    numposes;
    rate_r,
    rate_a,
    spine_t,
    kwargs...
)

```

Generate canonical helix graph that expands along a spiral pattern, analogous flower petals.

Notes

  * This function wraps the complex `spine_t(t)` function to generate the spiral pattern.

      * `rate_a` and `rate_r` can be varied for different spiral behavior.
  * See generalized helix generator for more details.
  * Defaults are choosen to slewto have multple trajectory intersects between consecutive loops of the helix and do a decent job of moving around coverage area with a relative balance of encircled area sizes.

Related 

[`generateGraph_Helix2D!`](@ref), [`generateGraph_Helix2DSlew!`](@ref)
