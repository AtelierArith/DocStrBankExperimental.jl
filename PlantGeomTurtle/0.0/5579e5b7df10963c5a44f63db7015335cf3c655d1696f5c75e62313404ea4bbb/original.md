```
Rectangle(turtle; length = 1.0, width = 1.0, move = false)
```

Generate a rectangle in front of the turtle and and return it.

## Arguments

  * `turtle`: The turtle that we feed the rectangle to.
  * `length`: Length of the rectangle.
  * `width`: Width of the rectangle.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).

## Details

A triangle mesh will be generated representing the rectangle. The rectangle will be generated in front of the turtle, on the plane defined by the arm and head axes of the turtle. The argument `length` refers to the axis of the rectangle aligned with the head axis of the turtle, whereas `width` refers to the orthogonal axis.

When `move = true`, the turtle will be moved forward by a distance equal to `length`.

## Return

Returns a triangular mesh (object of type `Mesh`).

## Examples

```jldoctest
julia> turtle = Turtle();

julia> r = Rectangle(turtle; length = 2.0, width = 1.0);
```
