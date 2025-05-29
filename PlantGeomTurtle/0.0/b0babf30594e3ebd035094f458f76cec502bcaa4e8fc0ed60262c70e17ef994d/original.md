```
Mesh(turtle, m::Mesh; scale = Vec(1.0, 1.0, 1.0), move = false)
```

Scale a pre-existing mesh by using the turtle's state.

## Arguments

  * `turtle`: The turtle that we feed the mesh to.
  * `m`: The pre-existing unscaled mesh in standard position and orientation.
  * `scale`: Vector with scaling factors for the x, y and z axes.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).

## Details

A pre-existing mesh will be scaled (acccording to `scale`), rotate so that it is oriented in the same direction as the turtle and translated so that the mesh is generated in front of the turtle. A deep copy of the original mesh is made prior to any transformation.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

## Return

Returns a triangular mesh (object of type `Mesh`).

## Examples

```jldoctest
julia> import PlantGeomPrimitives as PG

julia> e = PG.Ellipse();

julia> turtle = Turtle();

julia> ne = Mesh!(turtle, e, scale = PG.Vec(2.0, 2.0, 2.0));
```
