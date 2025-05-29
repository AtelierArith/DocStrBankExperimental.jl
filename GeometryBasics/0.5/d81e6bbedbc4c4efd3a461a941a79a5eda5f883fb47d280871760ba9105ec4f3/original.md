```
Mesh{PositionDim, PositionType, FaceType, VertexAttributeNames, VertexAttributeTypes, FaceVectorType} <: AbstractMesh{PositionDim, PositionType} <: AbstractGeometry{PositionDim, PositionType}
```

The type of a concrete mesh. The associated struct contains 3 fields:

```julia
struct Mesh{...}
    vertex_attributes::NamedTuple{VertexAttributeNames, VertexAttributeTypes}
    faces::FaceVectorType
    views::Vector{UnitRange{Int}}
end
```

A vertex typically carries multiple distinct pieces of data, e.g. a position, a normal, a texture coordinate, etc. We call those pieces of data vertex attributes. The `vertex_attributes` field contains the name and a collection `<: AbstractVector` or `<: FaceView` for each attribute. The n-th element of that collection is the value of the corresponding attribute for the n-th vertex.

```julia
#                   vertex       1        2        3
vertex_attributes[:position] = [pos1,    pos2,    pos3,    ...]
vertex_attributes[:normal]   = [normal1, normal2, normal3, ...]
...
```

A `NamedTuple` is used here to allow different meshes to carry different vertex attributes while also keeping things type stable. The constructor enforces a few restrictions:

  * The first attribute must be named `position` and must have a `Point{PositionDim, PositionType}` eltype.
  * Each vertex attribute must refer to the same number of vertices. (All vertex attributes defined by

AbstractVector must match in length. For FaceViews, the number of faces needs to match.)

See also: [`vertex_attributes`](@ref), [`coordinates`](@ref), [`normals`](@ref), [`texturecoordinates`](@ref), [`decompose`](@ref), [`FaceView`](@ref), [`expand_faceviews`](@ref)

The `faces` field is a collection `<: AbstractVector{FaceType}` containing faces that describe how vertices are connected. Typically these are `(GL)TriangleFace`s or `QuadFace`s, but they can be any collection of vertex indices `<: AbstractFace`.

See also: [`faces`](@ref), [`decompose`](@ref)

The `views` field can be used to separate the mesh into mutliple submeshes. Each submesh is described by a "view" into the `faces` vector, i.e. submesh n uses `mesh.faces[mesh.views[n]]`. A `Mesh` can be constructed without `views`, which results in an empty `views` vector.

See also: [`merge`](@ref), [`split_mesh`](@ref)
