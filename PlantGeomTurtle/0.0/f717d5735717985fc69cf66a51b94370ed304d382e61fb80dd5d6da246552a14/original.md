```
Ellipse(turtle; length = 1.0, width = 1.0, n = 20, move = false)
```

Generate an ellipse in front of a turtle and return it.

## Arguments

  * `turtle`: The turtle which state is used to create the ellipse.
  * `length`: Length of the ellipse.
  * `width`: Width of the ellipse.
  * `n`: Number of triangles of the mesh approximating the ellipse (an integer).
  * `move`: Whether to move the turtle forward or not (`true` or `false`).

## Details

A triangle mesh will be generated with `n` triangles that approximates an ellipse. The ellipse will be generated in front of the turtle, on the plane defined by the arm and head axes of the turtle. The argument `length` refers to the axis of the ellipse aligned with the head axis of the turtle, whereas `width` refers to the orthogonal axis.

When `move = true`, the turtle will be moved forward by a distance equal to `length`.

## Return

Returns a triangular mesh (object of type `Mesh`).

## Examples

```jldoctest
julia> turtle = Turtle();

julia> e = Ellipse(turtle; length = 1.0, width = 0.5, n = 40);
```
