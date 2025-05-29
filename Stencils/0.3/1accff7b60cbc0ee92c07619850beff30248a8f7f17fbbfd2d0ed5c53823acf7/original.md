```
Stencil <: StaticVector
```

Stencils define a pattern of neighboring cells around the current cell. They reduce the structure and dimensions of the neighborhood into a `StaticVector` of values.

Stencil objects are updated to contain the neighbors for an array index.

This design is so that user functions can be passed a single object from which they can retrieve center, neighbors, offsets, distances to neighbors and other information.

Stencils also provide a range of compile-time utility funcitons like `distances` and `offsets`.
