```
struct Rounded{T <: Coordinate} <: GeometryEntityStyle
    abs_r::T = zero(T)
    rel_r::Float64 = 0.0
    min_side_len::T = r
    min_angle::Float64 = 1e-3
    p0::Vector{Point{T}} = []
    inverse_selection::Bool = false
end
```

Rounded polygon style defined by either radius absolute radius `abs_r` or relative radius `rel_r`. Only one of `abs_r` or `rel_r` can be non-zero at once. Can't handle shapes with interior cuts, or shapes with too sharp of angles relative to segment length. If `rel_r` is non-zero the radius of curvature at each vertex is calculated with `rel_r * min(l₁, l₂)` where `l₁` and `l₂` denote the length of the two attached line segments.

Example usage:

```julia
r = Rectangle(10μm, 10μm)
rsty = Rounded(1μm)
# Create a rounded rectangle StyledEntity with different options for syntax
rounded_rect = rsty(r)
rounded_rect = styled(r, rsty)
rounded_rect = Rounded(r, 1μm)
# Turn the result into a plain Polygon
rounded_rect_discretized_poly = to_polygons(rounded_rect)
```

## Keyword arguments

  * `min_side_len`: The minimum side length that will get rounded (e.g. for 90-degree angles, it makes sense to have `min_side_len = 2 * rounding_radius`). This currently uses exact comparison, so it may result in very short straight edges or failure to round a corner due to floating point imprecision.
  * `min_angle`: If adjacent sides are collinear within the tolerance set by `min_angle`, rounding will not be performed.
  * `p0`: set of target points used to select vertices to attempt to round when applied to a polygon. Selected vertices where `min_side_len` and `min_angle` are satisfied will be rounded. If empty, all vertices will be selected. Otherwise, for each point in `p0`, the nearest point in the styled polygon will be selected. Note that for a `ClippedPolygon`, the same `p0` will be used for every contour; for different rounding styles on different contours, use `StyleDict`.
  * `inverse_selection`: If true, the selection from `p0` is inverted; that is, all corners will be rounded except those selected by `p0`.
