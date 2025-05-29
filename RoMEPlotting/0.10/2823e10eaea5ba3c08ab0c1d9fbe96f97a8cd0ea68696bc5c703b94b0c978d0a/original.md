```julia
plotSLAM2DPoses(
    fg;
    solveKey,
    regexPoses,
    from,
    to,
    variableList,
    meanmax,
    ppe,
    recalcPPEs,
    lbls,
    scale,
    x_off,
    y_off,
    drawhist,
    spscale,
    dyadScale,
    drawTriads,
    drawContour,
    levels,
    contour,
    line_width,
    drawPoints,
    pointsColor,
    drawEllipse,
    ellipseColor,
    manualColor
)

```

2D plot of all poses, assuming poses are labeled from ``::Symbol` type `:x0, :x1, ..., :xn`.  Use `to` and `from` to limit the range of numbers `n` to be drawn.  The underlying histogram can be enabled or disabled, and the size of maximum-point belief estimate cursors can be controlled with `spscale`.

Future:

  * Relax to user defined pose labeling scheme, for example `:p1, :p2, ...`
