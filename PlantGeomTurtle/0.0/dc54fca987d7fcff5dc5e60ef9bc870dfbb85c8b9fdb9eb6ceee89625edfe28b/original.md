```
Triangle!(turtle; length = 1.0, width = 1.0, move = false, kwargs...)
```

Generate a triangle in front of the turtle and feed it to a turtle.

## Arguments

  * `turtle`: The turtle that we feed the triangle to.
  * `length`: Length of the triangle.
  * `width`: Width of the triangle.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `kwargs`: Properties to be set per triangle in the mesh.

## Details

A triangle mesh will be generated representing the triangle. The triangle will be generated in front of the turtle, on the plane defined by the arm and head axes of the turtle. The argument `length` refers to the axis of the triangle aligned with the head axis of the turtle, whereas `width` refers to the orthogonal axis.

When `move = true`, the turtle will be moved forward by a distance equal to `length`.

## Return

Returns `nothing` but modifies the `turtle` as a side effect.

## Examples

```jldoctest
julia> turtle = Turtle();

julia> Triangle!(turtle; length = 2.0, width = 1.0);
```
