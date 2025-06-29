```
setfillrule(rule::Symbol)
```

Set the fill rule for paths for the current drawing.

`rule` can be `:winding` or `:even_odd`

The fill rule is used to select how subpaths are filled. For both fill rules, whether or not a point is included in the fill is determined by taking a ray from that point to infinity and looking at intersections with the path. The ray can be in any direction, as long as it doesn't pass through the end point of a segment or have a tricky intersection such as intersecting tangent to the path. (Note that filling is not actually implemented in this way. This is just a description of the rule that is applied.)

The default fill rule is `:winding`.

`:winding`: If the path crosses the ray from left-to-right, counts +1. If the path crosses the ray from right to left, counts -1. (Left and right are determined from the perspective of looking along the ray from the starting point.) If the total count is non-zero, the point will be filled.

`even_odd`: counts the total number of intersections, without regard to the orientation of the contour. If the total number of intersections is odd, the point will be filled. (Since 1.0)

See [`getfillrule`](@ref).
