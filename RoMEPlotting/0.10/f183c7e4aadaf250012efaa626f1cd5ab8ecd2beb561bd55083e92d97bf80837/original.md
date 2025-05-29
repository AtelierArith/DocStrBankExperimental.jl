```julia
plotPose(, pp; ...)
plotPose(
    ,
    pp,
    title;
    levels,
    c,
    legend,
    axis,
    scale,
    overlay,
    hdl
)

```

Plot pose belief as contour information on visually sensible manifolds.

Example:

```julia
fg = generateGraph_ZeroPose()
initAll!(fg);
plotPose(fg, :x0)
```

Related

[`plotSLAM2D`](@ref), [`plotSLAM2DPoses`](@ref), [`plotBelief`](@ref), `plotKDECircular`
