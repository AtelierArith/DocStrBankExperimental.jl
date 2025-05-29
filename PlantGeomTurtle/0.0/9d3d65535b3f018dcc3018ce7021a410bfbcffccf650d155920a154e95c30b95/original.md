```
Mesh!(turtle, m::Mesh; scale = Vec(1.0, 1.0, 1.0), move = false, transform = true,
      deepcopy = true, kwargs...)
```

Feed a pre-existing mesh to a turtle (with optional transformation).

## Arguments

  * `turtle`: The turtle that we feed the mesh to.
  * `m`: The pre-existing unscaled mesh in standard position and orientation.
  * `scale`: Vector with scaling factors for the x, y and z axes.
  * `move`: Whether to move the turtle forward or not (`true` or `false`).
  * `transform`: Whether to to transform the mesh according to the turtle's position and orientation the scaling vector provided by the user.
  * `deepcopy`: Whether to make a deep copy of the mesh before feeding it to the turtle.
  * `kwargs`: Properties to be set per triangle in the mesh.

## Details

A pre-existing mesh will be scaled (acccording to `scale`), rotate so that it is oriented in the same direction as the turtle and translated so that the mesh is generated in front of the turtle. A deep copy of the original mesh is made prior to any transformation.

When `move = true`, the turtle will be moved forward by a distance equal to `height`.

There are two expected use cases for this function:

1. When the user defines a *reference* mesh that is used to generate multiple instances of the same mesh with different scales at transformations. An example would be an ad-hoc mesh that represents the shape of a leaf. In this case, the user wants to set `transform = true` and `deepcopy = true`.
2. When the user generates a mesh using a primitive function that takes the turtle as argument, performs some operations on that mesh (e.g., calculating area, coordinates of the center, etc) and then feed that mesh into the turtle. In this case, the user wants to set `transform = false` (because the transformation was alread applied) and probably also `deepcopy = false` because the deepcopy is an unnecessary cost.

## Return

Returns `nothing` but modifies the `turtle` as a side effect.

## Examples

```jldoctest
julia> import PlantGeomPrimitives as PG

julia> e = PG.Ellipse();

julia> turtle = Turtle();

julia> Mesh!(turtle, e, scale = PG.Vec(2.0, 2.0, 2.0));
```
