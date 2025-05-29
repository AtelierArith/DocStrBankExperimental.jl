```julia
generateGraph_Circle(; ...)
generateGraph_Circle(
    poses;
    fg,
    offsetPoses,
    autoinit,
    graphinit,
    landmark,
    loopClosure,
    stopEarly,
    biasTurn,
    kappaOdo,
    cyclePoses
)

```

Generate a canonical factor graph: driving in a circular pattern with one landmark.

Notes

  * Poses, :x0, :x1,... Pose2,
  * Odometry, :x0x1f1, etc., Pose2Pose2 (Gaussian)
  * OPTIONAL: 1 Landmark, :l1, Point2,
  * 2 Sightings, :x0l1f1, :x6l1f1, RangeBearing (Gaussian)

Example

```julia
using RoME

fg = generateGraph_Hexagonal()
drawGraph(fg, show=true)
```

DevNotes

  * TODO refactor to use new `calcHelix_T`.

Related

[`generateGraph_Circle`](@ref), [`generateGraph_Kaess`](@ref), [`generateGraph_TwoPoseOdo`](@ref)
