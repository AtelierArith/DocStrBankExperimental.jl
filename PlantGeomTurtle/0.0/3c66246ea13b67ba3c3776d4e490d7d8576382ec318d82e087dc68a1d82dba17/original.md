```
SolidCylinder(turtle; length = 1.0, width = 1.0, height = 1.0, n = 80, move = false)
```

Generate a solid cylinder in front of the turtle and return it.

## Arguments

  * `turtle`: The turtle that we feed the solid cylinder to.
  * `length`: Length of the ellipse at the base of the solid cylinder.
  * `width`: Width of the ellipse at the base of the solid cylinder.
  * `height`: Height of the solid cylinder.
  * `n`: Number of triangles in the mesh (must be even).
  * `move`: Whether to move the turtle forward or not (`true` or `false`).

## Details

A mesh will be generated with n triangles that approximate the solid cylinder. The cylinder will be generated in front of the turtle, with the base on the plane defined by the arm and up axes of the turtle, centered at the head axis. The `length` argument refers to the up axis, whereas `width` refers to the arm axis and `height` is associated to the head axis.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

## Return

Returns a triangular mesh (object of type `Mesh`).

## Examples

```jldoctest
julia> turtle = Turtle();

julia> c = SolidCylinder(turtle; length = 1.0, width = 1.0, height = 2.0, n = 80);
```
