```julia
plotLocalProduct(
    fgl,
    lbl;
    solveKey,
    N,
    dims,
    levels,
    show,
    dirpath,
    mimetype,
    sidelength,
    title,
    xmin,
    xmax,
    ymin,
    ymax
)

```

Plot the proposal belief from neighboring factors to `lbl` in the factor graph (ignoring Bayes tree representation), and show with new product approximation for reference.

DevNotes

  * TODO, standardize around ::MIME="image/svg", see JuliaRobotics/DistributedFactorGraphs.jl#640
