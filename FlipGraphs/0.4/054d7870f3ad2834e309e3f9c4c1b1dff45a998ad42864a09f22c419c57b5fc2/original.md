```
struct TriFace
```

A `TriFace` represents a triangle in the triangulation of a surface. 

The `TriFace`s form the vertices of a DeltaComplex. Each `TriFace` is formed between 3 points and is connected to 3 `TriFace`s through `DualEdges`. The points and neighboring triangles do not have to be unique.

The points and edges are stored in an anticlockwise order.
The first edge/side is between the first and second point.
The second edge/side is between the second and third point.
The third edge/side is between the third and first point.

