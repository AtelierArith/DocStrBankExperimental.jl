```julia
plotSLAM2DLandmarks(
    fg;
    solveKey,
    regexLandmark,
    from,
    to,
    minnei,
    variableList,
    meanmax,
    ppe,
    recalcPPEs,
    lbls,
    showmm,
    scale,
    x_off,
    y_off,
    drawhist,
    drawContour,
    levels,
    contour,
    manualColor,
    c,
    MM,
    point_size,
    drawPoints,
    pointsColor,
    drawEllipse,
    ellipseColor,
    resampleGaussianFit
)

```

2D plot of landmarks, assuming `:l1, :l2, ... :ln`.  Use `from` and `to` to control the range of landmarks `n` to include.
