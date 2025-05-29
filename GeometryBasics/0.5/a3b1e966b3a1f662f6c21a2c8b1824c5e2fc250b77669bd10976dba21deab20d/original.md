```
decompose(::Type{TargetType}, primitive)
decompose(::Type{TargetType}, data::AbstractVector)
```

Dependent on the given type, extracts data from the primitive and converts its eltype to `TargetType`.

Possible `TargetType`s:

  * `<: Point` extracts and converts positions (calling `coordinates()`)
  * `<: AbstractFace` extracts and converts faces (calling `faces()`)
  * `<: Normal{<: Vec}` extracts and converts normals, potentially generating them (calling `normals()`)
  * `<: UV{<: Vec}` extracts and converts 2D texture coordinates, potentially generating them (calling `texturecoordinates()`)
  * `<: UVW{<: Vec}` extracts and converts 3D texture coordinates, potentially generating them (calling `texturecoordinates()`)
