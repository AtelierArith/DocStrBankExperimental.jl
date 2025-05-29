```julia
generateGraph_Helix2DSlew!(; ...)
generateGraph_Helix2DSlew!(
    numposes;
    slew_x,
    slew_y,
    spine_t,
    kwargs...
)

```

Generate canonical slewed helix graph (like a flattened slinky).

Notes

  * Use `slew_x` and `slew_y` to pull the "slinky" out in different directions at constant rate.
  * See generalized helix generator for more details.
  * Defaults are choosen to slew along x and have multple trajectory intersects between consecutive loops of the helix.

Related

[`generateGraph_Helix2D!`](@ref), [`generateGraph_Helix2DSpiral!`](@ref)
