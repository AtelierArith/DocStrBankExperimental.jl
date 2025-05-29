```
Ellipse!(turtle; length = 1.0, width = 1.0, n = 20, move = false, kwargs...)
```

Generate an ellipse in front of a turtle and feed it to a turtle.

## Arguments

  * `turtle`: The turtle that we feed the ellipse to.
  * `length`: Length of the ellipse.
  * `width`: Width of the ellipse.
  * `n`: Number of triangles of the mesh approximating the ellipse (an integer).
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `kwargs`: Properties to be set per triangle in the mesh.

## Details

A triangle mesh will be generated with `n` triangles that approximates an ellipse. The ellipse will be generated in front of the turtle, on the plane defined by the arm and head axes of the turtle. The argument `length` refers to the axis of the ellipse aligned with the head axis of the turtle, whereas `width` refers to the orthogonal axis.

When `move = true`, the turtle will be moved forward by a distance equal to `length`.

## Return

Returns `nothing` but modifies the `turtle` as a side effect.

## Examples

```jldoctest
julia> turtle = Turtle();

julia> Ellipse!(turtle; length = 1.0, width = 0.5, n = 40);
```
