```
intersection_point(pos₁::Point, pos₂::Point, bearing₁₃::Float64, bearing₂₃::Float64)
```

Return the intersection point `pos₃` [deg] of two great circle paths given two start points [deg] `pos₁` and `pos₂` [deg] and two bearings [deg] from `pos₁` to `pos₃` [deg], and from `pos₂` to `pos₃` [deg].

Under certain circumstances the results can be an ∞ or *ambiguous solution*.

Source: edwilliams.org/avform.htm
