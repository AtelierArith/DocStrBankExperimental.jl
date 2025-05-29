```julia
calcPosePointBearingRange(pose, poin)

```

Calculate a bearing and range parameter between Pose2 and Point2 `::Vector`s.

Example

```julia
b,r = calcPosePointBearingRange([0;0;0], [10;10])
```
