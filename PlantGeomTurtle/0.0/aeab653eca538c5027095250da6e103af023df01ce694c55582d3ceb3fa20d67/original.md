```
Trapezoid(turtle; length = 1.0, width = 1.0, ratio = 1.0, move = false)
```

Generate a trapezoid in front of the turtle and return it.

## Arguments

  * `turtle`: The turtle that we feed the trapezoid to.
  * `length`: Length of the trapezoid.
  * `width`: Width of the base of the trapezoid.
  * `ratio`: Ratio between the width of the top and base of the trapezoid.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).

## Details

A triangle mesh will be generated representing the trapezoid. The trapezoid will be generated in front of the turtle, on the plane defined by the arm and head axes of the turtle. The argument `length` refers to the axis of the trapezoid aligned with the head axis of the turtle, whereas `width` refers to the orthogonal axis.

When `move = true`, the turtle will be moved forward by a distance equal to `length`.

## Return

Returns a triangular mesh (object of type `Mesh`).

## Examples

```jldoctest
julia> turtle = Turtle();

julia> t = Trapezoid(turtle; length = 1.0, width = 1.0, ratio = 0.5);
```
