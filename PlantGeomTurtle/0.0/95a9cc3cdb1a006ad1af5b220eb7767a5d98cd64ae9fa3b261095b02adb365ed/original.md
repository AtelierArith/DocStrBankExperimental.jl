```
HollowCube(turtle; length = 1.0, width = 1.0, height = 1.0, move = false)
```

Generate a hollow cube in front of the turtle and return it.

## Arguments

  * `turtle`: The turtle that we feed the hollow cube to.
  * `length`: Length of the rectangle at the base of the hollow cube.
  * `width`: Width of the rectangle at the base of the hollow cube.
  * `height`: Height of the hollow cube.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).

## Details

A mesh will be generated of a hollow cube. The cube will be generated in front of the turtle, with the base on the plane defined by the arm and up axes of the turtle, centered at the head axis. The `length` argument refers to the up axis, whereas `width` refers to the arm axis and `height` is associated to the head axis.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

## Return

Returns a triangular mesh (object of type `Mesh`).

## Examples

```jldoctest
julia> turtle = Turtle();

julia> c = HollowCube(turtle; length = 1.0, width = 1.0, height = 2.0);
```
