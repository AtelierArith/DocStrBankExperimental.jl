```
Trapezoid!(turtle; length = 1.0, width = 1.0, ratio = 1.0, move = false, kwargs...)
```

Generate a trapezoid in front of the turtle and feed it to a turtle.

## Arguments

  * `turtle`: The turtle that we feed the trapezoid to.
  * `length`: Length of the trapezoid.
  * `width`: Width of the base of the trapezoid.
  * `ratio`: Ratio between the width of the top and base of the trapezoid.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `kwargs`: Properties to be set per triangle in the mesh.

## Details

A triangle mesh will be generated representing the trapezoid. The trapezoid will be generated in front of the turtle, on the plane defined by the arm and head axes of the turtle. The argument `length` refers to the axis of the trapezoid aligned with the head axis of the turtle, whereas `width` refers to the orthogonal axis.

When `move = true`, the turtle will be moved forward by a distance equal to `length`.

## Return

Returns `nothing` but modifies the `turtle` as a side effect.

## Examples

```jldoctest
julia> turtle = Turtle();

julia> Trapezoid!(turtle; length = 1.0, width = 1.0, ratio = 0.5);
```
