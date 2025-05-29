```
LocallyRefinedControlPoints(
    control_points_base,
    control_points_refined,
    local_refinements)
```

All data required to perform multiple refinement steps and overwriting control point values along the way, yielding a Truncated Hierarchical Basis (THB) spline.

## Fields

  * `control_points_base`: The densely defined control points at the basis of the hierarchy
  * `control_points_refined`: The intermediate and final control point arrays after applying the local refinements
  * `local_refinements`: Data for local refinement for each step in the hierarchy
