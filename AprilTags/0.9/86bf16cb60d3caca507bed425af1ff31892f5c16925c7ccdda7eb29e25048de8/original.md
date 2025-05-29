```julia
calcCornerProjectionsAprilTags!(
    cimg_,
    tags_;
    tagList,
    taglength,
    f_width,
    f_height,
    c_width,
    c_height,
    s,
    VERT,
    HORI,
    boardPattern,
    dodraw
)

```

April grid calibration helper function to assemble the cost for a single image. This function can also be used to draw the corner points on images  to show how the cost function is constructed as well as the calibration performance. See [`calcCalibResidualAprilTags!`](@ref) for details.
