```
read_ops_file(file)
```

Read the content of an `.ops` file and return a tuple with the scene dimensions and the object table.

# Arguments

  * `file::String`: Path of the `.ops` file to read.

# Returns

The scene dimensions and the object table as a tuple. The scene dimensions are a tuple of two `Meshes.Point` with the origin point and opposite point of the scene.  The object table is an array of `NamedTuple` with the following fields:

  * `sceneID::Int`: Scene ID.
  * `plantID::Int`: Plant ID.
  * `filePath::String`: Path to the `.opf` file.
  * `pos::Meshes.Point`: Position of the object.
  * `scale::Float64`: Scale of the object.
  * `inclinationAzimut::Float64`: Inclination azimut of the object.
  * `inclinationAngle::Float64`: Inclination angle of the object.
  * `rotation::Float64`: Rotation of the object.
  * `functional_group::String`: Functional group of the object.
