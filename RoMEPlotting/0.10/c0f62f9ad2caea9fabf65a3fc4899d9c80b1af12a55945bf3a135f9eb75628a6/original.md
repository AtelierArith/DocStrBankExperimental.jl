```julia
plotSLAM2D(
    fgl;
    solveKey,
    from,
    to,
    minnei,
    meanmax,
    posesPPE,
    landmsPPE,
    recalcPPEs,
    lbls,
    scale,
    x_off,
    y_off,
    drawTriads,
    dyadScale,
    levels,
    drawhist,
    MM,
    xmin,
    xmax,
    ymin,
    ymax,
    showmm,
    window,
    point_size,
    line_width,
    regexLandmark,
    regexPoses,
    variableList,
    manualColor,
    drawPoints,
    pointsColor,
    drawContour,
    drawEllipse,
    ellipseColor,
    title,
    aspect_ratio
)

```

2D plot of both poses and landmarks contained in factor graph.  Assuming poses and landmarks  are labeled `:x1, :x2, ...` and `:l0, :l1, ...`, respectively.  The range of numbers to  include can be controlled with `from` and `to` along with other keyword functionality for  manipulating the plot.

Notes

  * Assumes `:l1`, `:l2`, ... for landmarks –
  * Can increase default Gadfly plot size (for JSSVG in browser): `Gadfly.set_default_plot_size(35cm,20cm)`.
  * Enable or disable features such as the covariance ellipse with keyword `drawEllipse=true`.

DevNotes

  * TODO update to use e.g. `tags=[:LANDMARK]`,
  * TODO fix `drawHist`,
  * TODO deprecate, `showmm`, `spscale`.

Examples:

```julia
fg = generateGraph_Hexagonal()
plotSLAM2D(fg)
plotSLAM2D(fg, drawPoints=false)
plotSLAM2D(fg, contour=false, drawEllipse=true)
plotSLAM2D(fg, contour=false, title="SLAM result 1")

# or load a factor graph
fg_ = loadDFG("somewhere.tar.gz")
plotSLAM2D(fg_)
```

Related

[`plotSLAM2DPoses`](@ref), [`plotSLAM2DLandmarks`](@ref), [`plotPose`](@ref), [`plotBelief`](@ref) 
