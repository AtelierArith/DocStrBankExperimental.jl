```julia
plotLocalProductCylinder(
    fgl,
    lbl;
    N,
    levels,
    show,
    dirpath,
    mimetype,
    sidelength,
    scale
)

```

Plot–-for the cylindrical manifold only–-the proposal belief from neighboring factors to `lbl` in the factor graph (ignoring Bayes tree representation), and show with new product approximation for reference.  The linear and circular belief products are returned as a tuple.
