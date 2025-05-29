```
intersection_point(point₁::Point, point₂::Point, azimuth₁₃::Float64,
azimuth₂₃::Float64)
```

Return the intersection point `point₃` [deg] of two great circle lines given by two start points [deg] `point₁` and `point₂` [deg] and two azimuths [deg] from `point₁` to `point₃` [deg], and from `point₂` to `point₃` [deg].

Under certain circumstances the results can be an ∞ or *ambiguous solution*.

Source: edwilliams.org/avform.htm
